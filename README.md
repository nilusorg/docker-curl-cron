[![](https://images.microbadger.com/badges/image/jsonfry/curl-cron.svg)](https://microbadger.com/images/jsonfry/s3-sync "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/jsonfry/curl-cron.svg)](https://microbadger.com/images/jsonfry/s3-sync "Get your own version badge on microbadger.com")


# jsonfry/curl-cron

Docker image that runs periodically runs a curl command

## Usage

    docker run -d [OPTIONS] jsonfry/curl-cron


### Required Parameters:

* `-e OPTIONS=<OPTIONS>`: curl command options
* `-e CRON_SCHEDULE="0 1 * * *"`: specifies when cron job starts ([details](http://en.wikipedia.org/wiki/Cron)), e.g. `0 1 * * *` (runs every night at 1:00).

### Optional parameters:

* `now`: run container once and exit (no cron scheduling).

## Examples:

Run every 15 minutes with cron schedule (container keeps running):

    docker run -d \
        -e OPTIONS=example.com \
        -e CRON_SCHEDULE="*/15 * * * *" \
        elamonica/nilus:cron-curl

Run just once (container is deleted afterwards):

    docker run --rm \
        -e OPTIONS=example.com \
        elamonica/nilus:cron-curl now

