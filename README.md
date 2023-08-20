#Scevnin_Mihail_Final_Venus07
import requests

# URL для создания заказа
create_order_url = "https://814bf16a-d87c-4b7e-ba51-d98fbefb3f58.serverhub.praktikum-services.ru/api/v1/orders/create"

# URL для получения заказа по треку
get_order_url = "https://814bf16a-d87c-4b7e-ba51-d98fbefb3f58.serverhub.praktikum-services.ru/api/v1/orders/track/{}"

# Данные для создания заказа
order_data = {
    "firstName": "Michael",
    "lastName": "Jordan",
    "address": "Центральный проезд Хорошёвского Серебряного Бора 2",
    "metroStation": "Бульвар Адмирала Ушакова",
    "deliveryDate": "2023-08-09",
    "color": "BLACK",
    "comment": "Привет, МИР"
}

# Выполнение запроса на создание заказа
response = requests.post(create_order_url, json=order_data)
if response.status_code != 200:
    print("Failed to create order")
else:
    order_info = response.json()
    track = order_info["track"]
    print("Order created with track:", track)

    # Выполнение запроса на получение заказа по треку
    get_order_response = requests.get(get_order_url.format(track))
    if get_order_response.status_code == 200:
        print("Successfully retrieved order by track:", track)
    else:
        print("Failed to retrieve order by track:", track)
