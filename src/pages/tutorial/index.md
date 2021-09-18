# Austin 311 Complaints Summary

The analysis below investigates the frequency and nature of 311 calls in Austin, TX.

## Complaints by Day
```tracks_by_day
select
    date_completed,
    count(*) as tracks

from analytics.mart_quantified_self.fct_life_tracks

where date_completed is not null
 
group by 1
order by 1 desc
```

The most recent day of data was logged on <Value data={data.tracks_by_day} fmt=date/> and the number of complaints was <Value data={data.tracks_by_day} column="tracks"/>.

<LineChart 
    data={data.tracks_by_day} 
    x=date_completed
    y=tracks
/>

### Summary

### Daily Chart

## Complaints by Department
```tracks_by_name
select
    tracker_name,
    count(*) as tracks

from analytics.mart_quantified_self.fct_life_tracks

where tracker_name in ('slope_learning','book_read')

group by 1
order by 1 desc
```

{#each data.tracks_by_name as cbdept}

[{cbdept.tracker_name}](/tutorial/tracker_name/{cbdept.tracker_name}): <Value value={cbdept.tracks}/>

{/each}