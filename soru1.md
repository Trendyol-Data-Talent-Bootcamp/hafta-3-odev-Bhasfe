```SQL

select 
    name,
    car.id as car_id,
    car.model as car_model,
    manufacture.year as manufacture_year,
    array_agg(purchase.id) as purchase_id,
    array_agg(timestamp_add(purchase.date, interval 3 hour)) as purchase_date
from `dsmbootcamp.baris_hasdemir.semi_structured_hw`
cross join unnest(car) car
cross join unnest(manufacture) as manufacture
cross join unnest(purchase) as purchase
on car.id = manufacture.id
group by name, car_id, car_model, manufacture_year
order by name desc

```
