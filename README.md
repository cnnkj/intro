# intro


## tool 
* https://www.zotero.org/

## install plugin 
* Consensus

## nectec
การ สร้าง virtual env
```
python -m venv n2025
```
เปิด และ ปิด
```
n2025\Scripts\activate
n2025\Scripts\deactivate
```
การเตรียมการ
```
pip install streamlit httpx fastapi
```
การเก็บข้อมูล lib ที่จำเป็นและเตรียม deploy
```
pip freeze > requirements.txt
```
การสั่ง run
```
streamlit run main.py
```
