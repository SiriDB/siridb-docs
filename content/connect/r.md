---
title: "R"
weight: 22
---

R-connector for communicating with a SiriDB Database

### Installation

```{r}
install.packages('siridbr')
```

### Quick usage

```{r}
library(siridbr)

siridb <- SiriDB(
    user="iris",         # database user
    password="siri",     # password
    dbname="dbtest",     # database name
    server="localhost",  # server address
    port=9000L           # server port
)

siridb$connect(function(err) {
    # success: err is NULL
    # error:   err is a string with an error message
    if (!is.null(err)) {
        cat('Connection error: ', err)
    } else {
        siridb$close()
    }
})
```

### More info

A more complete description of the R-connector can be found via the link below.

- https://github.com/SiriDB/siridb-connector-r#readme
