# 🥤 Melanie's Smoothies

**A Custom Smoothie Ordering App**

An interactive web application built with **Streamlit** and **Snowflake (Snowpark)** that allows users to customize their smoothie orders and view real-time nutritional information. 

*Developed as part of the Snowflake Hands-On Essentials: Data Application Builders Workshop.*

---

## 🛠️ Tech Stack

- **Frontend & App Framework:** [Streamlit](https://streamlit.io/)
- **Data Platform:** [Snowflake](https://www.snowflake.com/) (via native Streamlit connections)
- **Data Engineering:** Snowpark & Pandas
- **External API Integration:** Python `requests` library

---

## ✨ Features

- **Dynamic Ingredient Selection:** Fetches available fruit options directly from the Snowflake database (`smoothies.public.fruit_options`), allowing users to pick up to 5 ingredients.
- **Live Nutritional Data:** Dynamically queries the SmoothieFroot REST API to display real-time nutritional facts for each selected fruit.
- **Smart Data Mapping:** Uses Pandas DataFrames for rapid, in-memory lookups (matching frontend selections to backend API search terms).
- **Order Persistence:** Securely writes the finalized custom order and customer name back into the Snowflake database (`smoothies.public.orders`).

---

## ⚙️ How It Works

1. **Session Initialization:** Connects to Snowflake using `st.connection("snowflake")`.
2. **Data Handling:** Queries tables using Snowpark and converts the output to a Pandas DataFrame for efficient array/location matching (`.loc`).
3. **API Integration:** Calls the external API dynamically based on the selected ingredients:
   ```python
   smoothiefroot_response = requests.get(f"[https://my.smoothiefroot.com/api/fruit/](https://my.smoothiefroot.com/api/fruit/){search_on}")
