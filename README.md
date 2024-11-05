# SQL Sorguları Açıklaması

Bu dosya, belirli SQL sorgularının ne işe yaradığını ve sonuçlarının nasıl yorumlanabileceğini açıklamaktadır. Aşağıda sorgular sırasıyla detaylandırılmıştır.

## 1. Soru: Film Tablosundaki Farklı Rating Değerlerini Listeleme

```sql
SELECT rating FROM film
GROUP BY rating;
```
Bu sorgu, film tablosunda bulunan rating sütunundaki farklı değerleri listeler. GROUP BY ifadesi ile rating sütunundaki benzersiz (unique) değerleri döndürür. Sonuç olarak, tablodaki tüm benzersiz rating değerlerini görmemizi sağlar.

2. Soru: Film Tablosunda Replacement Cost Değeri 50'den Fazla Olan Grupları Listeleme
```sql
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
```
Bu sorgu, film tablosunda replacement_cost (değiştirme maliyeti) sütununa göre gruplama yaparak her bir replacement_cost değeri için kaç adet film olduğunu sayar. HAVING COUNT(*) > 50 koşulu sayesinde sadece replacement_cost değeri 50'den fazla olan grupları döndürür.

3. Soru: Müşterilerin Mağazalara Göre Dağılımı
```sql
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
```
Bu sorgu, customer (müşteri) tablosundaki store_id sütununa göre gruplama yaparak her mağazada kaç müşteri olduğunu gösterir. Her bir store_id için müşteri sayısını listeleyerek mağazalara göre müşteri dağılımını görmemizi sağlar.

4. Soru: En Yüksek Country ID Değerine Sahip Ülkenin Şehir Sayısı
```sql
SELECT MAX(country_id), COUNT(*) FROM city
GROUP BY country_id
ORDER BY MAX(country_id) DESC
LIMIT 1;
```
Bu sorgu, city tablosundaki country_id sütununa göre gruplama yaparak her bir ülke için şehir sayısını hesaplar. MAX(country_id) ifadesi ile her bir gruptaki country_id değerlerinin en yükseğini alır. ORDER BY MAX(country_id) DESC ile bu değerleri azalan sırada sıralar ve LIMIT 1 ile en yüksek country_id değerine sahip ülkenin şehir sayısını döndürür.
