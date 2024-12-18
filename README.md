# StudentHub 

##  安裝與執行指引
### **1. 下載專案**
首先，將專案從 GitHub 複製到您的本地機器：
```bash
複製程式碼
git clone https://github.com/yourusername/StudentHub.git
cd StudentHub
```
### **2. 安裝前端依賴**
進入 frontend 目錄並安裝所需的 npm 套件：
```bash
複製程式碼
cd frontend
npm install
```
啟動前端開發伺服器：

```bash
複製程式碼
npm start
```
前端應用將會運行在 http://localhost:2888。

### **3. 安裝後端依賴**
進入 backend 目錄並安裝所需的 npm 套件：
```bash
複製程式碼
cd backend
npm install
```
### **4. 設定 MongoDB**
確保您已經安裝並啟動了 MongoDB。如果使用 MongoDB Atlas 或其他雲端資料庫，請在 .env 檔案中設定資料庫連接 URL。
```bash
複製程式碼
MONGO_URI=mongodb://localhost:27017/studenthub
```
### **5. 啟動後端伺服器**
在 backend 目錄啟動後端伺服器：
```bash
複製程式碼
npm start
```
後端將會運行在 http://localhost:5173。

### **6. 完成**
現在，您可以在瀏覽器中打開前端頁面並開始使用應用程式。

## API 規格說明
以下是本專案中提供的 API 規格，包括請求方式、請求參數及回應格式。
### 1.查詢所有學生資料
+ **使用到的URL**
+ `http://localhost:2888/api/v1/user/findAll`
+ ###### 取得的Response
    - 
        ```json
        {
            "code": 200,
            "message": "find sucess",
            "body": [
                {
                    "_id": "6761a9da059b9c65a4204fbf",
                    "userName": "tkuee0787",
                    "sid": "1",
                    "name": "張佳慧",
                    "department": "電機工程系",
                    "grade": "四年級",
                    "class": "A",
                    "email": "tkuee0787@tkuim.com"
                },
                {
                    "_id": "6761a9da059b9c65a4204fc0",
                    "userName": "tkubm9553",
                    "sid": "2",
                    "name": "蔡文杰",
                    "department": "企業管理系",
                    "grade": "二年級",
                    "class": "A",
                    "email": "tkubm9553@tkuim.com"
                },...
            ]
        }
        ```
### 2.根據 ID 查詢學生資料
+ **使用到的URL**
    + `http://localhost:2888/api/v1/user/findById`
+ ###### 取得的Request

    ```
    id": "6761a9da059b9c65a4204fc0
    ```

+ ###### 取得的Response
    - 
        ```json
        {
            "code": 200,
            "message": "find success",
            "body": {
                "_id": "6761a9da059b9c65a4204fc0",
                "userName": "tkubm9553",
                "sid": "2",
                "name": "蔡文杰",
                "department": "企業管理系",
                "grade": "二年級",
                "class": "A",
                "email": "tkubm9553@tkuim.com"
            }
        }
        ```
    
### 3.新增學生資料
+ **使用到的URL**
    + `http://localhost:2888/api/v1/user/findByName`
+ ###### 取得的Request
    ```json
    {
        "userName":"tku1567",
        "name": "王國全",
        "department": "資訊管理系",
        "grade": "六年級",
        "class": "B",
        "email": "tkume1567@tku.com"
    }
    ```
+ ###### 取得的Response
    - 
        ```json
        {
            "code": 200,
            "message": "insert success",
            "body": {
                       "userName":"tku1567",
                       "name": "王國全",
                       "department": "資訊管理系",
                       "grade": "六年級",
                       "class": "B",
                       "email": "tkume1567@tku.com",
                       "_id": "6762998299d3334a529baafe"
            }
        }
        ```
    
### 4.利用ID來刪除學生資料
+ **使用到的URL** 
    + `http://localhost:2888/api/v1/user/deletedById`
+ ###### 取得的Request
    ```
    id=675ed9f4bc8f2ebc70989e03
    ```
+ ###### 取得的Response
    - 
        ```json
        {
            "code": 200,
            "message": "sucess",
            "body": {
                "acknowledged": true,
                "deletedCount": 1
            }
        }
        ```
  
### 5.利用ID來更新學生資料
+ **使用到的URL**
    + `http://localhost:2888/api/v1/user/updateById`
+ ###### 取得的Request
  -
    ```
    id=675ed9f4bc8f2ebc70989e03
    ```
  -  
    更改的部分
    ```json
    {
        "姓名:卓家全",
    }
    ```
+ ###### 取得的Response
    - 
        ```json
        {
            "code": 200,
            "message": "Update successful",
            "body": {
                "_id": "675ed9f4bc8f2ebc70989e03",
                "userName": "tkumb1234",
                "sid": "1",
                "name": "張佳慧",
                "department": "風險管理系",
                "grade": "四年級",
                "class": "A",
                "email": "tkuee0787@tkuim.com"
            }
        }
