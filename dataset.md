# Docs Api Dataset
#### post [{API_URL}/v1/dataset]()
Tạo dataset cho từ 1 đến 3 tables

```bash
request.body:
{
  "dataSource": "string",
  "justOneTable": "string",
  "tables": [
    {
      "tableName": "Grade",
      "keyPreference": "AssignmentId",
      "keyTo": "id",
      "to": "Assignment"
    }
  ]
}
```
- Authenticate
- Tạo cho 1 table: Truyền vào **dataSource** (Id Connection info) và **justOneTable** (tên của table muốn tạo)
- Tạo cho 2 hoặc 3 table: truyền vào field **tables** với **tableName** - Tên table, **keyPreference** khóa liên kết của tableName, **to**: tên table được reference tới, **keyTo**: key của table được preference.

ví dụ:

##### Chỉ một table

```bash
request.body
{
  "dataSource": "622f4b642384d9153978c567",
  "justOneTable": "Comment"
}
```

##### 2 Table

```bash
request.body
{
  "dataSource": "622f4b642384d9153978c567",
  "tables": [
    {
      "tableName": "Grade",
      "keyPreference": "AssignmentId",
      "keyTo": "id",
      "to": "Assignment"
    }
  ]
}
```

##### 3 Table (miễn sao có khóa liên kết giữa 3 table)

```bash
request.body
{
  "dataSource": "622f4b642384d9153978c567",
  "tables": [
    {
      "tableName": "Grade",
      "keyPreference": "AssignmentId",
      "keyTo": "id",
      "to": "Assignment"
    },
    {
      "tableName": "Grade",
      "keyPreference": "ClassId",
      "keyTo": "id",
      "to": "Class"
    }
  ]
}
```

# Docs Api Dataset
#### get [{API_URL}/v1/dataset/{id}]()
export ra tất cả các cột của table trong dataset

```bash
request.params:
{
  "id": "6230c8adbea4bd0f5aab59d5"
}
```
- Authenticate
- Nhập vào Id dataset user đã tạo

example result

```bash
[
  {
    "id": 2,
    "studentId": "18120546",
    "fullName": "Mai Thien Tam",
    "point": 3,
    "isCompleted": true,
    "AssignmentId": 2,
    "ClassId": 2,
    "name": "Đồ án",
    "NO": 1
  },
  {
    "id": 3,
    "studentId": "18120546",
    "fullName": "Mai Thien Tam",
    "point": 6,
    "isCompleted": true,
    "AssignmentId": 3,
    "ClassId": 2,
    "name": "Thi cuối kỳ",
    "NO": 2
  },
  {
    "id": 1,
    "studentId": "18120546",
    "fullName": "Mai Thien Tam",
    "point": 1,
    "isCompleted": true,
    "AssignmentId": 1,
    "ClassId": 2,
    "name": "Bài tập",
    "NO": 0
  }
]
```
