# 🥤 Melanie's Smoothies

An end-to-end data application built with **Streamlit** and **Snowflake (Snowpark)** managing custom smoothie ordering and internal kitchen fulfillment.

*Snowflake Hands-On Essentials: Data Application Builders Workshop.*

---

## 🏗️ Architecture

- **Customer App (SniS):** External Streamlit app to customize smoothies, fetch live nutritional facts via REST API, and submit orders to Snowflake.
- **Kitchen Dashboard (SiS):** Internal app running natively inside Snowflake to manage pending orders (`ORDER_FILLED = 0`) and bulk-update status using `st.data_editor` and Snowpark `merge`.

---

## 🛠️ Tech Stack

- **Framework:** Streamlit & Streamlit in Snowflake (SiS)
- **Data Platform:** Snowflake & Snowpark Python API
- **Libraries:** Pandas, Requests

---

## 🔄 Workflow

1. **Ordering (SniS):** Customer selects up to 5 fruits $\rightarrow$ App queries external API for nutrition info $\rightarrow$ Order is inserted into Snowflake.
2. **Fulfillment (SiS):** Kitchen staff views pending orders natively in Snowflake $\rightarrow$ Updates completion status $\rightarrow$ Database merges changes in real time.
