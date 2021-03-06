# Apache Bench

https://www.devside.net/wamp-server/load-testing-apache-with-ab-apache-bench

```bash
$ ab -k -c 350 -n 20000 example.com/
```

By issuing the command above, you will be hitting http://example.com/ with 350 simultaneous connections until 20 thousand requests are met. It will be done using the keep alive header.

+ -k :This does the "KeepAlive" funcionality browsers do by nature.
+ -c :("Concurrency"). Indicates how many clients (people/users) will be hitting the site at the same time.
+ -n : Indicates how many requests are going to be made


## 1 concurrent user doing 100 page hits

This is 100 sequential page loads by a single user:
```bash
$ ab -l -r -n 100 -c 1 -k -H "Accept-Encoding: gzip, deflate" http://www.example.com/blog/
```

## 5 concurrent users each doing 10 page hits

This is 50 page loads (total) by 5 different concurrent users, each user is doing 10 sequential pages loads.
```bash
$ ab -l -r -n 50 -c 5 -k -H "Accept-Encoding: gzip, deflate" http://www.example.com/blog/
```

## 10 concurrent users each doing 10 page hits

This is 100 page loads by 10 different concurrent users, each user is doing 10 sequential pages loads.
```bash
ab -l -r -n 100 -c 10 -k -H "Accept-Encoding: gzip, deflate" http://www.example.com/blog/
```

## 90 concurrent users each doing 30 page hits

This is 2700 page loads by 90 different concurrent users, each user is doing 30 sequential pages loads.
```bash
$ ab -n 2700 -c 90 -k -H "Accept-Encoding: gzip, deflate" http://www.example.com/blog/
```

## Posting with apache ab
```
# post_loc.txt contains the json you want to post
# -p means to POST it
# -H adds an Auth header (could be Basic or Token)
# -T sets the Content-Type
# -c is concurrent clients
# -n is the number of requests to run in the test

ab -p post_loc.txt -T application/json -H 'Authorization: Token abcd1234' -c 10 -n 2000 http://example.com/api/v1/locations
```
