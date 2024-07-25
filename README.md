# listenbrainz-openapi

This project aims to provide an OpenAPI 3 specification for the [ListenBrainz API](https://listenbrainz.readthedocs.io/en/latest/users/api/index.html#reference).

## Structure

The specification is split up in multiple folders and files. Here is an overview of the folders:


```yaml
.
├── components              # holds data models
│   ├── art
│   ├── common
│   ├── core
│   ├── metadata
│   ├── playlists
│   ├── popularity
│   ├── recommendations
│   ├── recordings
│   ├── social
│   └── stats
└── paths                   # holds API endpoints
    ├── art
    ├── core
    ├── metadata
    ├── misc
    ├── playlists
    ├── popularity
    ├── recommendations
    ├── recordings
    ├── social
    └── stats
```

For each category of the ListenBrainz API, there is a folder under `components` and `paths`.

`components` contains the data models and `paths` the API endpoints.

On top sits the `lb.yaml` which holds everything together.


## Coverage

Even if the goal is to include every endpoint in this specification, some things are missing:

### Playlists

 * `/1/playlist/(playlist_mbid)/xspf`
 * `/1/playlist/(playlist_mbid)/export/(service)`
 * `/1/playlist/import/(service)`
 * `/1/playlist/(service)/(playlist_id)/tracks`
 * `/1/playlist/export-jspf/(service)`

### Recordings

 * `/1/feedback/import`

## Code generation

Client code for the API can be generated with the [OpenAPI Generator](https://openapi-generator.tech/docs/installation).

To generate a Java client:

```sh
openapi-generator generate -g java -i ./lb.yaml -o ./output/ -c config.json --additional-properties=useSingleRequestParameter=true
```

To set and validate the ListenBrainz user token:

```java
LbCoreApi core = new LbCoreApi();
core.getApiClient().setApiKey("Token mySecretToken");
core.validateToken().execute()
```

## Contributing

Contributing is welcome!

