# STARTHAON_PICT

### **📌 Comprehensive README.md for GitHub**  
This **README.md** file will guide users (including judges) through the complete setup, execution, and usage of the project, from **Solr activation** to running the **Streamlit UI**.

---

## **📄 README.md**
📍 Save this as **`README.md`** in the project root directory before pushing to GitHub.

```md
# 🚀 Apache Solr Data Indexing & Metadata Extraction with Streamlit UI

## 📌 Overview
This project provides an **interactive Streamlit UI** to manage **Apache Solr** efficiently.  
It allows users to **index JSON data**, **extract metadata**, **execute queries**, and **retrieve documents** in an easy-to-use interface.

✅ **Key Features**:
- **📊 Solr Metadata Extraction**
- **📂 Index JSON Data into Solr**
- **🔍 Search & Retrieve Documents**
- **🎨 Interactive Streamlit UI**
- **⚙️ Automation of Complex JSON Processing**

---

## **📂 Project Directory Structure**
```
C:\solr_project\
│── app.py                   # Streamlit UI for Solr

│── solr_metadata_extractor.py # Extract metadata & documents

│── solr_json_transformer.py  # Convert complex JSON for Solr

│── data.json                 # Sample data for indexing

│── solr_fixed.json           # Transformed JSON for Solr

│── solr_metadata.json        # Extracted metadata output

│── solr_metadata2.json       # Sample complex metadata

│── solr_metrics.db           # Solr database (if applicable)

│── requirements.txt          # Dependencies for setup

│── README.md                 # Complete project instructions


# **🔹 1. Install & Start Apache Solr**
## **📥 Step 1: Download & Install**
1. Download Apache Solr from:  
   👉 [https://solr.apache.org/downloads.html](https://solr.apache.org/downloads.html)
2. Extract it to `C:\Users\acer\Downloads\solr-9.8.0`.
3. Open **Command Prompt** and navigate to Solr `bin`:

   sh
   cd C:\Users\acer\Downloads\solr-9.8.0\bin
   

## **▶ Step 2: Start Solr**
```sh
solr start
```
To run Solr in the foreground for debugging:
```sh
solr start -f
```

## **📌 Step 3: Verify Solr is Running**
Open the browser:  
👉 **[http://localhost:8983/solr](http://localhost:8983/solr)**  
If Solr is running, the admin UI should be visible.

## **📌 Step 4: Create a Solr Core**
A **core** is where Solr stores indexed data. Create a core named `mycore`:
```sh
solr create -c mycore
```
List existing cores:
```sh
solr list
```

---

# **🔹 2. Index Data into Solr**
## **📥 Step 1: Prepare JSON Data**
Use `data.json` as an example:
```json
[
    {
        "id": "1",
        "title": "First Document",
        "author": "Alice",
        "category": "Tech"
    },
    {
        "id": "2",
        "title": "Second Document",
        "author": "Bob",
        "category": "Science"
    }
]
```

## **📌 Step 2: Upload JSON Data to Solr**
Run:
```sh
Invoke-WebRequest -Uri "http://localhost:8983/solr/mycore/update?commit=true" `
    -Method Post `
    -Headers @{"Content-Type" = "application/json"} `
    -InFile "C:\solr_project\data.json"
```

## **📌 Step 3: Verify Indexed Data**
Check indexed data:
```sh
Invoke-WebRequest -Uri "http://localhost:8983/solr/mycore/select?q=*:*&wt=json&indent=true" | Select-Object -ExpandProperty Content
```

---

# **🔹 3. Extract Solr Metadata Using Python**
## **📌 Step 1: Install Dependencies**
Run:
```sh
pip install -r C:\solr_project\requirements.txt
```

## **📌 Step 2: Run the Metadata Extraction Script**
```sh
python C:\solr_project\solr_metadata_extractor.py
```
This generates `solr_metadata.json` containing:
```json
{
    "core_name": "mycore",
    "index_size_bytes": 10538,
    "num_documents": 4,
    "sample_documents": [
        {
            "id": "2",
            "title": ["Second Document"],
            "author": ["Bob"],
            "category": ["Science"]
        },
        {
            "id": "3",
            "title": ["Third Document"],
            "author": ["Charlie"],
            "category": ["History"]
        }
    ]
}
```

---

# **🔹 4. Run the Streamlit UI**
## **📌 Step 1: Start the UI**
Run:
```sh
cd C:\solr_project
streamlit run app.py
```
This opens an interactive web app in your browser.

## **📌 Step 2: Features of the UI**
✅ Fetch **Solr Metadata** 📊  
✅ Extract **Sample Documents** 📝  
✅ Upload & Index **JSON Data** 📂  
✅ Secure **Login Authentication** 🔑  

---

# **🔹 5. Transform Complex JSON for Solr**
For complex JSON, use `solr_json_transformer.py`:
```sh
python C:\solr_project\solr_json_transformer.py
```
This converts `solr_metadata2.json` into `solr_fixed.json` for indexing.

---

# **🔹 6. Executing Queries in Solr**
Run queries via the **Solr Admin Panel**  
👉 Open: **[http://localhost:8983/solr/#/mycore/query](http://localhost:8983/solr/#/mycore/query)**  
Example Query:  
```
q=*:*&wt=json&rows=10
```

To filter by category:
```
q=category:Tech&wt=json&indent=true
```

---

# **🔹 7. Troubleshooting**
### ❌ **Solr Not Starting?**
```sh
solr restart
```
Or check logs:
```sh
solr status
```

### ❌ **Cannot Connect to Solr?**
Ensure Solr is running at:
```sh
http://localhost:8983/solr
```

### ❌ **Dependencies Not Found?**
Reinstall:
```sh
pip install -r requirements.txt
```

---

# **📌 Summary**
✔ **Installed Solr & Created a Core**  
✔ **Indexed JSON Data into Solr**  
✔ **Extracted Metadata using Python**  
✔ **Launched a Streamlit UI for Solr**  
✔ **Transformed & Indexed Complex JSON Data**  
✔ **Executed Queries in Solr**  

---

# 🎯 **Next Steps**
- **Improve Streamlit UI** with real-time updates 📊  
- **Automate batch indexing** of JSON files 🔄  
- **Add advanced search filters** for querying data 🔍  

---

# **💡 Contributing**
Want to improve this project? Feel free to **fork** and contribute! 🤝

---

# **📄 License**
This project is licensed under **Apache License 2.0**.

---

### 🎉 **Happy Searching with Solr! 🚀**
