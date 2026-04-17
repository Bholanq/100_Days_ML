API are basically data pipelines
When you call an API, they return data from a database.

```
import requests
response = requests.get("http://api.themoviedb.org/3/movie/top_rated?api_key=261626528b292bb31a2a06f5f75d5ade&language=en-US&page=1")

df = pd.DataFrame(response.json()['results'])[['id','title','overview','release_date','popularity','vote_average','vote_count']]

for i in range(1,10):
    response = requests.get(f"http://api.themoviedb.org/3/movie/top_rated?api_key=261626528b292bb31a2a06f5f75d5ade&language=en-US&page={i}")
    temp_df = pd.DataFrame(response.json()['results'])[['id','title','overview','release_date','popularity','vote_average','vote_count']]
    df = pd.concat([df, temp_df], ignore_index=True)
    
```