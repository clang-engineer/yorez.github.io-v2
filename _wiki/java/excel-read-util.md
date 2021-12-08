---
layout  : wiki
title   : java에서 엑셀 파일 읽기 
summary : 
date    : 2021-11-21 21:30:57 +0900
updated : 2021-12-08 10:32:16 +0900
tags    : 
toc     : true
public  : true
parent  : [[java/index]]
latex   : false
---
* TOC
{:toc}

# Apache Poi 라이브러리로 엑셀 파일 읽어오기

## 의존성 추가
```gradle
implementation group: 'org.apache.poi', name: 'poi', version: '4.1.2'
implementation group: 'org.apache.poi', name: 'poi-ooxml', version: '4.1.2'
```

##  excel util
### 시트의 각 행을 key-value list(List<Map<String, Object>>)형태로 읽어옴
```java
public class ExcelUtils {
    private static final Logger log = LoggerFactory.getLogger(ExcelUtils.class);

    public static Workbook getWorkbookFromStream(InputStream targetStream, String extension) throws Exception {
        log.debug("Read workbook from {}", targetStream);

        checkExcelExtension(extension);

        Workbook workbook = null;
        try {
            if (extension.equals("xlsx")) {
                workbook = new XSSFWorkbook(targetStream);
            } else if (extension.equals("xls")) {
                workbook = new HSSFWorkbook(targetStream);
            }
        } catch (InvalidFormatException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }

        return workbook;
    }

    private static void checkExcelExtension(String extension) throws Exception {
        if (!extension.equals("xlsx") && !extension.equals("xls")) {
            throw new IOException("엑셀 아닙니다.");
        }
    }

    public static List<Map<String, Object>> readSheet(Workbook workbook, String sheetName) throws Exception {
        log.debug("Read sheet name : {}", sheetName);

        Sheet sheet = workbook.getSheet(sheetName);

        if (sheet == null) {
            sheet = workbook.getSheetAt(0);
        }

        Row header = sheet.getRow(ExcelConstants.HEADER_ROW_NUMBER);

        List<Map<String, Object>> result = new ArrayList<>();

        for (int rowIndex = 2; rowIndex < sheet.getLastRowNum() + 1; rowIndex++) {
            Row row = sheet.getRow(rowIndex);
            if (isNotEmptyCell(row.getCell(0))) {
                Map<String, Object> keymapfiedRow = getHeaderRowWeaved(header, row);
                keymapfiedRow.put("excelRowNum", rowIndex);
                result.add(keymapfiedRow);
            }
        }
        return result;
    }

    public static LinkedHashMap<String, Object> readRow(Workbook workbook, String sheetName, int rowNum) throws Exception {
        log.debug("Read {} row num : {}", sheetName, rowNum);

        Sheet sheet = workbook.getSheet(sheetName);

        if (sheet == null) {
            sheet = workbook.getSheetAt(0);
        }

        Row header = sheet.getRow(ExcelConstants.HEADER_ROW_NUMBER);
        Row targetRow = sheet.getRow(rowNum);

        return getHeaderRowWeaved(header, targetRow);
    }

    private static LinkedHashMap<String, Object> getHeaderRowWeaved(Row header, Row row) {
        LinkedHashMap<String, Object> result = new LinkedHashMap<>();
        for (int columnIndex = 0; columnIndex <= header.getLastCellNum(); columnIndex++) {
            Cell headerCell = header.getCell(columnIndex);
            if (isNotEmptyCell(headerCell)) {
                Cell cell = row.getCell(columnIndex);
                result.put((String) readCell(headerCell), readCell(cell));
            }
        }

        return result;
    }

    private static boolean isNotEmptyCell(Cell cell) {
        return cell != null && !cell.toString().isBlank();
    }

    private static Object readCell(Cell cell) {
        log.debug("Read cell : {}", cell.getStringCellValue());

        Object value = null;

        if (cell == null) {
            return value;
        }

        if (cell.getCellType() == CellType.NUMERIC && DateUtil.isCellDateFormatted(cell)) {
            return cell.getDateCellValue().toInstant().atZone(ZoneId.systemDefault()).toLocalDate();
        }

        switch (cell.getCellType()) {
            case FORMULA:
                CellType type = cell.getCachedFormulaResultType();
                if (type == CellType.NUMERIC) {
                    value = cell.getNumericCellValue();
                } else {
                    value = cell.getStringCellValue();
                }
                break;
            case NUMERIC:
                value = cell.getNumericCellValue();
                break;
            case BOOLEAN:
                value = cell.getBooleanCellValue();
                break;
            case ERROR:
                value = cell.getErrorCellValue();
                break;
            case BLANK:
                value = null;
                break;
            default:
                value = cell.getStringCellValue();
                break;
        }

        return value;
    }

}
```
