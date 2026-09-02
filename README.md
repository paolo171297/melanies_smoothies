# 🥤 Melanie's Smoothies

An end-to-end data application built with **Streamlit** and **Snowflake (Snowpark)** managing custom smoothie ordering and internal kitchen fulfillment.

*Snowflake Hands-On Essentials: Data Application Builders Workshop.*

---

## 🏗️ Architecture

- **Customer App (SniS):** External Streamlit app to customize smoothies, fetch live nutritional facts via REST API (`my.smoothiefroot.com`), and submit orders to Snowflake.
- **Kitchen Dashboard (SiS):** Internal app running natively inside Snowflake to manage pending orders (`ORDER_FILLED = 0`) and bulk-update status using `st.data_editor` and Snowpark `merge`.

---

## 🛠️ Tech Stack

- **Framework:** Streamlit & Streamlit in Snowflake (SiS)
- **Data Platform:** Snowflake & Snowpark Python API
- **Data Processing:** Pandas, Requests

---

## ⚙️ Core Operations

```python
# 1. Customer API Lookup (SniS)
smoothiefroot_response = requests.get(f"[https://my.smoothiefroot.com/api/fruit/](https://my.smoothiefroot.com/api/fruit/){search_on}")

# 2. Kitchen Fulfillment Merge (SiS)
og_dataset.merge(
    edited_dataset,
    (og_dataset['ORDER_UID'] == edited_dataset['ORDER_UID']),
    [when_matched().update({'ORDER_FILLED': edited_dataset['ORDER_FILLED']})]
)
