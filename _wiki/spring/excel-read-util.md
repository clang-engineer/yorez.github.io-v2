---
layout  : wiki
title   : spring에서 엑셀 파일 읽기 
summary : 
date    : 2021-11-21 21:30:57 +0900
updated : 2021-11-21 21:41:29 +0900
tags    : 
toc     : true
public  : true
parent  : 
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

    public static List<Map<String, Object>> readExcel(MultipartFile file) throws Exception {
        Workbook workbook = readWorkbook(file);

        Sheet sheet = workbook.getSheetAt(0);
        Row header = sheet.getRow(0);

        List<Map<String, Object>> result = new ArrayList<>();

        for (int rowIndex = 1; rowIndex < sheet.getLastRowNum() + 1; rowIndex++) {
            Row row = sheet.getRow(rowIndex);
            if (isNotEmptyCell(row.getCell(0))) {
                Map<String, Object> keymapfiedRow = getKeymapfiedRow(header, row);
                log.info(rowIndex + "row : " + keymapfiedRow);
                result.add(keymapfiedRow);
            }
        }
        return result;
    }

    private static boolean isNotEmptyCell(Cell cell) {
        return cell != null && !cell.toString().isBlank();
    }

    private static Map<String, Object> getKeymapfiedRow(Row header, Row row) {
        Map<String, Object> result = new HashMap<>();
        for (int columnIndex = 0; columnIndex <= header.getLastCellNum(); columnIndex++) {
            Cell headerCell = header.getCell(columnIndex);
            if (isNotEmptyCell(headerCell)) {
                Cell cell = row.getCell(columnIndex);
                result.put(readCell(headerCell), readCell(cell));
            }
        }

        return result;
    }

    private static Workbook readWorkbook(MultipartFile file) throws Exception {
        String extension = FilenameUtils.getExtension(file.getOriginalFilename());
        if (file.isEmpty()) {
            throw new IOException("파일 선택하세요");
        }

        if (!extension.equals("xlsx") && !extension.equals("xls")) {
            throw new IOException("엑셀 아닙니다.");
        }

        Workbook workbook = null;

        try {
            if (extension.equals("xlsx")) {
                workbook = new XSSFWorkbook(file.getInputStream());
            } else if (extension.equals("xls")) {
                workbook = new HSSFWorkbook(file.getInputStream());
            }
        } catch (InvalidFormatException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }

        return workbook;
    }

    private static String readCell(Cell cell) {

        String value = "";

        if (cell == null) {
            return value;
        }

        switch (cell.getCellType()) {
            case STRING:
                value = cell.getStringCellValue();
                break;
            case NUMERIC:
                value = (int) cell.getNumericCellValue() + "";
                break;
            default:
                break;
        }
        return value;
    }
}
```
