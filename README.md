# Sparta_coding

  ## 2021.06.07
  * sparta_coding data analysis week 01 complete

``
# 1주차 과제 (피자 데이터)
# Q1. 피자를 가장 많이 시켜먹는 요일은 언제인가요?

import pandas as pd
import matplotlib.pyplot as plt

pizza_data = pd.read_csv('./data/pizza_09.csv')
pizza_calls_data = pizza_data.groupby('요일')['통화건수'].sum()

weeks = ['월', '화', '수', '목', '금', '토', '일']
sorted_pizza_calls_data = pizza_calls_data.sort_values(ascending=True).reindex(weeks)

# graph
plt.figure(figsize=(10,5))
plt.bar(sorted_pizza_calls_data.index, sorted_pizza_calls_data)
plt.title('요일별 피자 총 주문 수')
plt.xlabel('요일')
plt.ylabel('주문 수')
plt.show()

print('피자를 가장 많이 시켜먹는 요일 : 일요일')

# Q2. 피자를 가장 많이 시켜먹는 구는 어디인가요?

pizza_calls_data_for_place = pizza_data.groupby('발신지_구')['통화건수'].sum()
sorted_pizza_calls_data_for_place = pizza_calls_data_for_place.sort_values(ascending=True)

# graph
plt.figure(figsize=(10,5))
plt.bar(sorted_pizza_calls_data_for_place.index, sorted_pizza_calls_data_for_place)
plt.title('구별 피자 총 주문 수')
plt.xlabel('서울특별시 구')
plt.ylabel('주문 수')
plt.xticks(rotation=45)
plt.show()

print('피자를 가장 많이 시켜먹는 구 : 강서구')

# 바 그래프 2개 그리기
# 요일별 치킨 및 피자 총 주문 수
chicken07 = pd.read_csv('./data/chicken_07.csv')
chicken08 = pd.read_csv('./data/chicken_08.csv')
chicken09 = pd.read_csv('./data/chicken_09.csv')
chicken_data = pd.concat([chicken07, chicken08, chicken09])
sum_of_calls_by_week = chicken_data.groupby('요일')['통화건수'].sum().reindex(weeks)
sorted_sum_of_calls_by_week = sum_of_calls_by_week.sort_values(ascending=True)

plt.bar(sorted_sum_of_calls_by_week.index, sorted_sum_of_calls_by_week)
plt.bar(pizza_calls_data.index, pizza_calls_data)
plt.title('요일별 치킨 및 피자 총 주문 수')
plt.xlabel('요일')
plt.ylabel('주문 수')
plt.legend(['치킨 주문 수','피자 주문 수'])
plt.show()

![1](https://user-images.githubusercontent.com/47622991/121136646-d88ddc00-c870-11eb-842e-fbfd2985fd83.PNG)
![2](https://user-images.githubusercontent.com/47622991/121136641-d75caf00-c870-11eb-9fba-d2aefed11838.PNG)
![3](https://user-images.githubusercontent.com/47622991/121136644-d88ddc00-c870-11eb-9236-0d082eaa5580.PNG)
