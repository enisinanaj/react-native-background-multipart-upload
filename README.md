# react-native-background-multipart-upload
React Native module for multipart chunked uploader in a background task

This is meant for uploading a file in a background task using react-native for both iOS and Android devices. It will use a persistent storage to keep a queue of files to upload.

Will be configurable to whether start uploading with the queue right at application start or on a manual basis from the user interface.


### Configuration

.....


### API

* init(config: Configuration)
* startUpload(): Promise
* addFileToQueue(file: FileType): Promise


### Events

* onUpload(progress: ProgressType)


### Types

`Configuration`

| Field  | Type | Default | Description |
| ------------- | ------------- | ------------- | ------------- |
| `chunkSize`  | Number  | 1024 * 1024 * 1024 * 10 | Size of single chunks to upload. The files will be separated in chunks of this size before upload |
| `continuousUpload`  | Boolean  | true | If set to `true`, the uplaod of the queue will start/continue at application startUp |
| `endpointUrl`  | String  | N/A | URL of the endpoint to send videos to |
| `deleteFileAfterUpload`  | Boolean  | true | Delete a file after successful upload |
| `progressStep`  | Number  | 0.1 | How often to get the event `onProgress` triggered |
....


`FileType`

| Field  | Type | Default | Description |
| ------------- | ------------- | ------------- | ------------- |
| `name`  | String  | N/A | Name of the file. Will be sent as the filename of the chunk part section of the multipart request | 
| `path`  | String  | N/A | Path of the file to upload (e.g. `file:///....`) |
| `id`  | String  | N/A | Identifier for the file in order to know in the `onProgress` event which file is the progress about. |
....


`ProgressType`

| Field  | Type | Description |
| ------------- | ------------- | ------------- |
| `progress`  | Number | Progress from *0.0* to *1.0* | 
| `currentChunk` | Number | The current chunk being uploaded. [1..totalNumberOfChunks] |
....


### TODO

At the moment all the code base is inside another react-native application. I'll publish it as soon as I take it out of the app into a standalone module.

1. Create standalone module
2. Persist queue to app storage
3. Create `react-native` facade for the native module.

### License

For the license I'm open to suggestions. Didn't actually read what the MIT license has to offer but I've seen it used often.
