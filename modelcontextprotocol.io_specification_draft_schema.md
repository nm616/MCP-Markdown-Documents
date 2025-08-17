---
url: "https://modelcontextprotocol.io/specification/draft/schema"
title: "Schema Reference - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Draft

Search...

Ctrl K

Search...

Navigation

Schema Reference

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Common Types](https://modelcontextprotocol.io/specification/draft/schema#common-types)
- [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations)
- [AudioContent](https://modelcontextprotocol.io/specification/draft/schema#audiocontent)
- [BlobResourceContents](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents)
- [BooleanSchema](https://modelcontextprotocol.io/specification/draft/schema#booleanschema)
- [ClientCapabilities](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities)
- [ContentBlock](https://modelcontextprotocol.io/specification/draft/schema#contentblock)
- [Cursor](https://modelcontextprotocol.io/specification/draft/schema#cursor)
- [EmbeddedResource](https://modelcontextprotocol.io/specification/draft/schema#embeddedresource)
- [EmptyResult](https://modelcontextprotocol.io/specification/draft/schema#emptyresult)
- [EnumSchema](https://modelcontextprotocol.io/specification/draft/schema#enumschema)
- [ImageContent](https://modelcontextprotocol.io/specification/draft/schema#imagecontent)
- [Implementation](https://modelcontextprotocol.io/specification/draft/schema#implementation)
- [JSONRPCError](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcerror)
- [JSONRPCNotification](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcnotification)
- [JSONRPCRequest](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcrequest)
- [JSONRPCResponse](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcresponse)
- [LoggingLevel](https://modelcontextprotocol.io/specification/draft/schema#logginglevel)
- [ModelHint](https://modelcontextprotocol.io/specification/draft/schema#modelhint)
- [ModelPreferences](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences)
- [NumberSchema](https://modelcontextprotocol.io/specification/draft/schema#numberschema)
- [PrimitiveSchemaDefinition](https://modelcontextprotocol.io/specification/draft/schema#primitiveschemadefinition)
- [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken)
- [Prompt](https://modelcontextprotocol.io/specification/draft/schema#prompt)
- [PromptArgument](https://modelcontextprotocol.io/specification/draft/schema#promptargument)
- [PromptMessage](https://modelcontextprotocol.io/specification/draft/schema#promptmessage)
- [PromptReference](https://modelcontextprotocol.io/specification/draft/schema#promptreference)
- [RequestId](https://modelcontextprotocol.io/specification/draft/schema#requestid)
- [Resource](https://modelcontextprotocol.io/specification/draft/schema#resource)
- [ResourceContents](https://modelcontextprotocol.io/specification/draft/schema#resourcecontents)
- [ResourceLink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink)
- [ResourceTemplate](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate)
- [ResourceTemplateReference](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplatereference)
- [Result](https://modelcontextprotocol.io/specification/draft/schema#result)
- [Role](https://modelcontextprotocol.io/specification/draft/schema#role)
- [Root](https://modelcontextprotocol.io/specification/draft/schema#root)
- [SamplingMessage](https://modelcontextprotocol.io/specification/draft/schema#samplingmessage)
- [ServerCapabilities](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities)
- [StringSchema](https://modelcontextprotocol.io/specification/draft/schema#stringschema)
- [TextContent](https://modelcontextprotocol.io/specification/draft/schema#textcontent)
- [TextResourceContents](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents)
- [Tool](https://modelcontextprotocol.io/specification/draft/schema#tool)
- [ToolAnnotations](https://modelcontextprotocol.io/specification/draft/schema#toolannotations)
- [completion/complete](https://modelcontextprotocol.io/specification/draft/schema#completion%2Fcomplete)
- [CompleteRequest](https://modelcontextprotocol.io/specification/draft/schema#completerequest)
- [CompleteResult](https://modelcontextprotocol.io/specification/draft/schema#completeresult)
- [elicitation/create](https://modelcontextprotocol.io/specification/draft/schema#elicitation%2Fcreate)
- [ElicitRequest](https://modelcontextprotocol.io/specification/draft/schema#elicitrequest)
- [ElicitResult](https://modelcontextprotocol.io/specification/draft/schema#elicitresult)
- [initialize](https://modelcontextprotocol.io/specification/draft/schema#initialize)
- [InitializeRequest](https://modelcontextprotocol.io/specification/draft/schema#initializerequest)
- [InitializeResult](https://modelcontextprotocol.io/specification/draft/schema#initializeresult)
- [logging/setLevel](https://modelcontextprotocol.io/specification/draft/schema#logging%2Fsetlevel)
- [SetLevelRequest](https://modelcontextprotocol.io/specification/draft/schema#setlevelrequest)
- [notifications/cancelled](https://modelcontextprotocol.io/specification/draft/schema#notifications%2Fcancelled)
- [CancelledNotification](https://modelcontextprotocol.io/specification/draft/schema#cancellednotification)
- [notifications/initialized](https://modelcontextprotocol.io/specification/draft/schema#notifications%2Finitialized)
- [InitializedNotification](https://modelcontextprotocol.io/specification/draft/schema#initializednotification)
- [notifications/message](https://modelcontextprotocol.io/specification/draft/schema#notifications%2Fmessage)
- [LoggingMessageNotification](https://modelcontextprotocol.io/specification/draft/schema#loggingmessagenotification)
- [notifications/progress](https://modelcontextprotocol.io/specification/draft/schema#notifications%2Fprogress)
- [ProgressNotification](https://modelcontextprotocol.io/specification/draft/schema#progressnotification)
- [notifications/prompts/list\_changed](https://modelcontextprotocol.io/specification/draft/schema#notifications%2Fprompts%2Flist-changed)
- [PromptListChangedNotification](https://modelcontextprotocol.io/specification/draft/schema#promptlistchangednotification)
- [notifications/resources/list\_changed](https://modelcontextprotocol.io/specification/draft/schema#notifications%2Fresources%2Flist-changed)
- [ResourceListChangedNotification](https://modelcontextprotocol.io/specification/draft/schema#resourcelistchangednotification)
- [notifications/resources/updated](https://modelcontextprotocol.io/specification/draft/schema#notifications%2Fresources%2Fupdated)
- [ResourceUpdatedNotification](https://modelcontextprotocol.io/specification/draft/schema#resourceupdatednotification)
- [notifications/roots/list\_changed](https://modelcontextprotocol.io/specification/draft/schema#notifications%2Froots%2Flist-changed)
- [RootsListChangedNotification](https://modelcontextprotocol.io/specification/draft/schema#rootslistchangednotification)
- [notifications/tools/list\_changed](https://modelcontextprotocol.io/specification/draft/schema#notifications%2Ftools%2Flist-changed)
- [ToolListChangedNotification](https://modelcontextprotocol.io/specification/draft/schema#toollistchangednotification)
- [ping](https://modelcontextprotocol.io/specification/draft/schema#ping)
- [PingRequest](https://modelcontextprotocol.io/specification/draft/schema#pingrequest)
- [prompts/get](https://modelcontextprotocol.io/specification/draft/schema#prompts%2Fget)
- [GetPromptRequest](https://modelcontextprotocol.io/specification/draft/schema#getpromptrequest)
- [GetPromptResult](https://modelcontextprotocol.io/specification/draft/schema#getpromptresult)
- [prompts/list](https://modelcontextprotocol.io/specification/draft/schema#prompts%2Flist)
- [ListPromptsRequest](https://modelcontextprotocol.io/specification/draft/schema#listpromptsrequest)
- [ListPromptsResult](https://modelcontextprotocol.io/specification/draft/schema#listpromptsresult)
- [resources/list](https://modelcontextprotocol.io/specification/draft/schema#resources%2Flist)
- [ListResourcesRequest](https://modelcontextprotocol.io/specification/draft/schema#listresourcesrequest)
- [ListResourcesResult](https://modelcontextprotocol.io/specification/draft/schema#listresourcesresult)
- [resources/read](https://modelcontextprotocol.io/specification/draft/schema#resources%2Fread)
- [ReadResourceRequest](https://modelcontextprotocol.io/specification/draft/schema#readresourcerequest)
- [ReadResourceResult](https://modelcontextprotocol.io/specification/draft/schema#readresourceresult)
- [resources/subscribe](https://modelcontextprotocol.io/specification/draft/schema#resources%2Fsubscribe)
- [SubscribeRequest](https://modelcontextprotocol.io/specification/draft/schema#subscriberequest)
- [resources/templates/list](https://modelcontextprotocol.io/specification/draft/schema#resources%2Ftemplates%2Flist)
- [ListResourceTemplatesRequest](https://modelcontextprotocol.io/specification/draft/schema#listresourcetemplatesrequest)
- [ListResourceTemplatesResult](https://modelcontextprotocol.io/specification/draft/schema#listresourcetemplatesresult)
- [resources/unsubscribe](https://modelcontextprotocol.io/specification/draft/schema#resources%2Funsubscribe)
- [UnsubscribeRequest](https://modelcontextprotocol.io/specification/draft/schema#unsubscriberequest)
- [roots/list](https://modelcontextprotocol.io/specification/draft/schema#roots%2Flist)
- [ListRootsRequest](https://modelcontextprotocol.io/specification/draft/schema#listrootsrequest)
- [ListRootsResult](https://modelcontextprotocol.io/specification/draft/schema#listrootsresult)
- [sampling/createMessage](https://modelcontextprotocol.io/specification/draft/schema#sampling%2Fcreatemessage)
- [CreateMessageRequest](https://modelcontextprotocol.io/specification/draft/schema#createmessagerequest)
- [CreateMessageResult](https://modelcontextprotocol.io/specification/draft/schema#createmessageresult)
- [tools/call](https://modelcontextprotocol.io/specification/draft/schema#tools%2Fcall)
- [CallToolRequest](https://modelcontextprotocol.io/specification/draft/schema#calltoolrequest)
- [CallToolResult](https://modelcontextprotocol.io/specification/draft/schema#calltoolresult)
- [tools/list](https://modelcontextprotocol.io/specification/draft/schema#tools%2Flist)
- [ListToolsRequest](https://modelcontextprotocol.io/specification/draft/schema#listtoolsrequest)
- [ListToolsResult](https://modelcontextprotocol.io/specification/draft/schema#listtoolsresult)

## [​](https://modelcontextprotocol.io/specification/draft/schema\#common-types)  Common Types

### [​](https://modelcontextprotocol.io/specification/draft/schema\#annotations)  `Annotations`

interfaceAnnotations{

[audience](https://modelcontextprotocol.io/specification/draft/schema#annotations-audience)?: [Role](https://modelcontextprotocol.io/specification/draft/schema#role)\[\];

[lastModified](https://modelcontextprotocol.io/specification/draft/schema#annotations-lastmodified)?:string;

[priority](https://modelcontextprotocol.io/specification/draft/schema#annotations-priority)?:number;

}

Optional annotations for the client. The client can use annotations to inform how objects are used or displayed

`Optional` audience [Permalink](https://modelcontextprotocol.io/specification/draft/schema#annotations-audience)

audience?: [Role](https://modelcontextprotocol.io/specification/draft/schema#role)\[\]

Describes who the intended customer of this object or data is.

It can include multiple entries to indicate content useful for multiple audiences (e.g., `[“user”, “assistant”]`).

`Optional` lastModified [Permalink](https://modelcontextprotocol.io/specification/draft/schema#annotations-lastmodified)

lastModified?:string

The moment the resource was last modified, as an ISO 8601 formatted string.

Should be an ISO 8601 formatted string (e.g., “2025-01-12T15:00:58Z”).

Examples: last activity timestamp in an open file, timestamp when the resource
was attached, etc.

`Optional` priority [Permalink](https://modelcontextprotocol.io/specification/draft/schema#annotations-priority)

priority?:number

Describes how important this data is for operating the server.

A value of 1 means “most important,” and indicates that the data is
effectively required, while 0 means “least important,” and indicates that
the data is entirely optional.

TJS-type [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tjs-type)

number

### [​](https://modelcontextprotocol.io/specification/draft/schema\#audiocontent)  `AudioContent`

interfaceAudioContent{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#audiocontent-_meta)?:{\[key:string\]:unknown};

[annotations](https://modelcontextprotocol.io/specification/draft/schema#audiocontent-annotations)?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations);

[data](https://modelcontextprotocol.io/specification/draft/schema#audiocontent-data):string;

[mimeType](https://modelcontextprotocol.io/specification/draft/schema#audiocontent-mimetype):string;

[type](https://modelcontextprotocol.io/specification/draft/schema#):“audio”;

}

Audio provided to or from an LLM.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#audiocontent-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` annotations [Permalink](https://modelcontextprotocol.io/specification/draft/schema#audiocontent-annotations)

annotations?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations)

Optional annotations for the client.

data [Permalink](https://modelcontextprotocol.io/specification/draft/schema#audiocontent-data)

data:string

The base64-encoded audio data.

mimeType [Permalink](https://modelcontextprotocol.io/specification/draft/schema#audiocontent-mimetype)

mimeType:string

The MIME type of the audio. Different providers may support different audio types.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#blobresourcecontents)  `BlobResourceContents`

interfaceBlobResourceContents{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents-_meta)?:{\[key:string\]:unknown};

[blob](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents-blob):string;

[mimeType](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents-mimetype)?:string;

[uri](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents-uri):string;

}

The contents of a specific resource or sub-resource.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

blob [Permalink](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents-blob)

blob:string

A base64-encoded string representing the binary data of the item.

`Optional` mimeType [Permalink](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents-mimetype)

mimeType?:string

The MIME type of this resource, if known.

uri [Permalink](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents-uri)

uri:string

The URI of this resource.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#booleanschema)  `BooleanSchema`

interfaceBooleanSchema{

[default](https://modelcontextprotocol.io/specification/draft/schema#)?:boolean;

[description](https://modelcontextprotocol.io/specification/draft/schema#)?:string;

[title](https://modelcontextprotocol.io/specification/draft/schema#)?:string;

[type](https://modelcontextprotocol.io/specification/draft/schema#):“boolean”;

}

### [​](https://modelcontextprotocol.io/specification/draft/schema\#clientcapabilities)  `ClientCapabilities`

interfaceClientCapabilities{

[elicitation](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities-elicitation)?:object;

[experimental](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities-experimental)?:{\[key:string\]:object};

[roots](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities-roots)?:{listChanged?:boolean};

[sampling](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities-sampling)?:object;

}

Capabilities a client may support. Known capabilities are defined here, in this schema, but this is not a closed set: any client can define its own, additional capabilities.

`Optional` elicitation [Permalink](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities-elicitation)

elicitation?:object

Present if the client supports elicitation from the server.

`Optional` experimental [Permalink](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities-experimental)

experimental?:{\[key:string\]:object}

Experimental, non-standard capabilities that the client supports.

`Optional` roots [Permalink](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities-roots)

roots?:{listChanged?:boolean}

Present if the client supports listing roots.

Type declaration

- `Optional` listChanged?: boolean



Whether the client supports notifications for changes to the roots list.


`Optional` sampling [Permalink](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities-sampling)

sampling?:object

Present if the client supports sampling from an LLM.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#contentblock)  `ContentBlock`

ContentBlock:

\| [TextContent](https://modelcontextprotocol.io/specification/draft/schema#textcontent)

\| [ImageContent](https://modelcontextprotocol.io/specification/draft/schema#imagecontent)

\| [AudioContent](https://modelcontextprotocol.io/specification/draft/schema#audiocontent)

\| [ResourceLink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink)

\| [EmbeddedResource](https://modelcontextprotocol.io/specification/draft/schema#embeddedresource)

### [​](https://modelcontextprotocol.io/specification/draft/schema\#cursor)  `Cursor`

Cursor:string

An opaque token used to represent a cursor for pagination.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#embeddedresource)  `EmbeddedResource`

interfaceEmbeddedResource{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#embeddedresource-_meta)?:{\[key:string\]:unknown};

[annotations](https://modelcontextprotocol.io/specification/draft/schema#embeddedresource-annotations)?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations);

[resource](https://modelcontextprotocol.io/specification/draft/schema#): [TextResourceContents](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents) \| [BlobResourceContents](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents);

[type](https://modelcontextprotocol.io/specification/draft/schema#):“resource”;

}

The contents of a resource, embedded into a prompt or tool call result.

It is up to the client how best to render embedded resources for the benefit
of the LLM and/or the user.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#embeddedresource-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` annotations [Permalink](https://modelcontextprotocol.io/specification/draft/schema#embeddedresource-annotations)

annotations?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations)

Optional annotations for the client.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#emptyresult)  `EmptyResult`

EmptyResult: [Result](https://modelcontextprotocol.io/specification/draft/schema#result)

A response that indicates success but carries no data.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#enumschema)  `EnumSchema`

interfaceEnumSchema{

[description](https://modelcontextprotocol.io/specification/draft/schema#)?:string;

[enum](https://modelcontextprotocol.io/specification/draft/schema#):string\[\];

[enumNames](https://modelcontextprotocol.io/specification/draft/schema#)?:string\[\];

[title](https://modelcontextprotocol.io/specification/draft/schema#)?:string;

[type](https://modelcontextprotocol.io/specification/draft/schema#):“string”;

}

### [​](https://modelcontextprotocol.io/specification/draft/schema\#imagecontent)  `ImageContent`

interfaceImageContent{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#imagecontent-_meta)?:{\[key:string\]:unknown};

[annotations](https://modelcontextprotocol.io/specification/draft/schema#imagecontent-annotations)?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations);

[data](https://modelcontextprotocol.io/specification/draft/schema#imagecontent-data):string;

[mimeType](https://modelcontextprotocol.io/specification/draft/schema#imagecontent-mimetype):string;

[type](https://modelcontextprotocol.io/specification/draft/schema#):“image”;

}

An image provided to or from an LLM.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#imagecontent-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` annotations [Permalink](https://modelcontextprotocol.io/specification/draft/schema#imagecontent-annotations)

annotations?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations)

Optional annotations for the client.

data [Permalink](https://modelcontextprotocol.io/specification/draft/schema#imagecontent-data)

data:string

The base64-encoded image data.

mimeType [Permalink](https://modelcontextprotocol.io/specification/draft/schema#imagecontent-mimetype)

mimeType:string

The MIME type of the image. Different providers may support different image types.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#implementation)  `Implementation`

interfaceImplementation{

[name](https://modelcontextprotocol.io/specification/draft/schema#implementation-name):string;

[title](https://modelcontextprotocol.io/specification/draft/schema#implementation-title)?:string;

[version](https://modelcontextprotocol.io/specification/draft/schema#):string;

}

Describes the name and version of an MCP implementation, with an optional title for UI representation.

name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#implementation-name)

name:string

Intended for programmatic or logical use, but used as a display name in past specs or fallback (if title isn’t present).

`Optional` title [Permalink](https://modelcontextprotocol.io/specification/draft/schema#implementation-title)

title?:string

Intended for UI and end-user contexts — optimized to be human-readable and easily understood,
even by those unfamiliar with domain-specific terminology.

If not provided, the name should be used for display (except for Tool,
where `annotations.title` should be given precedence over using `name`,
if present).

### [​](https://modelcontextprotocol.io/specification/draft/schema\#jsonrpcerror)  `JSONRPCError`

interfaceJSONRPCError{

[error](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcerror-error):{code:number;data?:unknown;message:string};

[id](https://modelcontextprotocol.io/specification/draft/schema#): [RequestId](https://modelcontextprotocol.io/specification/draft/schema#requestid);

[jsonrpc](https://modelcontextprotocol.io/specification/draft/schema#):“2.0”;

}

A response to a request that indicates an error occurred.

error [Permalink](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcerror-error)

error:{code:number;data?:unknown;message:string}

Type declaration

- code: number



The error type that occurred.

- `Optional` data?: unknown



Additional information about the error. The value of this member is defined by the sender (e.g. detailed error information, nested errors etc.).

- message: string



A short description of the error. The message SHOULD be limited to a concise single sentence.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#jsonrpcnotification)  `JSONRPCNotification`

interfaceJSONRPCNotification{

[jsonrpc](https://modelcontextprotocol.io/specification/draft/schema#):“2.0”;

[method](https://modelcontextprotocol.io/specification/draft/schema#):string;

[params](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcnotification-params)?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown};

}

A notification which does not expect a response.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcnotification-params)

params?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown}

Type declaration

- \[key: string\]:unknown

- `Optional`\_meta?: {\[key:string\]:unknown}



See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#jsonrpcrequest)  `JSONRPCRequest`

interfaceJSONRPCRequest{

[id](https://modelcontextprotocol.io/specification/draft/schema#): [RequestId](https://modelcontextprotocol.io/specification/draft/schema#requestid);

[jsonrpc](https://modelcontextprotocol.io/specification/draft/schema#):“2.0”;

[method](https://modelcontextprotocol.io/specification/draft/schema#):string;

[params](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcrequest-params)?:{

\_meta?:{progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);\[key:string\]:unknown};

\[key:string\]:unknown;

};

}

A request that expects a response.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#jsonrpcrequest-params)

params?:{

\_meta?:{progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);\[key:string\]:unknown};

\[key:string\]:unknown;

}

Type declaration

- \[key: string\]:unknown

- `Optional`\_meta?: {progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);\[key:string\]:unknown}



See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.





  - `Optional` progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken)



    If specified, the caller is requesting out-of-band progress notifications for this request (as represented by notifications/progress). The value of this parameter is an opaque token that will be attached to any subsequent notifications. The receiver is not obligated to provide these notifications.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#jsonrpcresponse)  `JSONRPCResponse`

interfaceJSONRPCResponse{

[id](https://modelcontextprotocol.io/specification/draft/schema#): [RequestId](https://modelcontextprotocol.io/specification/draft/schema#requestid);

[jsonrpc](https://modelcontextprotocol.io/specification/draft/schema#):“2.0”;

[result](https://modelcontextprotocol.io/specification/draft/schema#): [Result](https://modelcontextprotocol.io/specification/draft/schema#result);

}

A successful (non-error) response to a request.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#logginglevel)  `LoggingLevel`

LoggingLevel:

\|“debug”

\|“info”

\|“notice”

\|“warning”

\|“error”

\|“critical”

\|“alert”

\|“emergency”

The severity of a log message.

These map to syslog message severities, as specified in RFC-5424: [https://datatracker.ietf.org/doc/html/rfc5424#section-6.2.1](https://datatracker.ietf.org/doc/html/rfc5424#section-6.2.1)

### [​](https://modelcontextprotocol.io/specification/draft/schema\#modelhint)  `ModelHint`

interfaceModelHint{

[name](https://modelcontextprotocol.io/specification/draft/schema#modelhint-name)?:string;

}

Hints to use for model selection.

Keys not declared here are currently left unspecified by the spec and are up
to the client to interpret.

`Optional` name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#modelhint-name)

name?:string

A hint for a model name.

The client SHOULD treat this as a substring of a model name; for example:

- `claude-3-5-sonnet` should match `claude-3-5-sonnet-20241022`
- `sonnet` should match `claude-3-5-sonnet-20241022`, `claude-3-sonnet-20240229`, etc.
- `claude` should match any Claude model

The client MAY also map the string to a different provider’s model name or a different model family, as long as it fills a similar niche; for example:

- `gemini-1.5-flash` could match `claude-3-haiku-20240307`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#modelpreferences)  `ModelPreferences`

interfaceModelPreferences{

[costPriority](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences-costpriority)?:number;

[hints](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences-hints)?: [ModelHint](https://modelcontextprotocol.io/specification/draft/schema#modelhint)\[\];

[intelligencePriority](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences-intelligencepriority)?:number;

[speedPriority](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences-speedpriority)?:number;

}

The server’s preferences for model selection, requested of the client during sampling.

Because LLMs can vary along multiple dimensions, choosing the “best” model is
rarely straightforward. Different models excel in different areas—some are
faster but less capable, others are more capable but more expensive, and so
on. This interface allows servers to express their priorities across multiple
dimensions to help clients make an appropriate selection for their use case.

These preferences are always advisory. The client MAY ignore them. It is also
up to the client to decide how to interpret these preferences and how to
balance them against other considerations.

`Optional` costPriority [Permalink](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences-costpriority)

costPriority?:number

How much to prioritize cost when selecting a model. A value of 0 means cost
is not important, while a value of 1 means cost is the most important
factor.

TJS-type [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tjs-type)

number

`Optional` hints [Permalink](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences-hints)

hints?: [ModelHint](https://modelcontextprotocol.io/specification/draft/schema#modelhint)\[\]

Optional hints to use for model selection.

If multiple hints are specified, the client MUST evaluate them in order
(such that the first match is taken).

The client SHOULD prioritize these hints over the numeric priorities, but
MAY still use the priorities to select from ambiguous matches.

`Optional` intelligencePriority [Permalink](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences-intelligencepriority)

intelligencePriority?:number

How much to prioritize intelligence and capabilities when selecting a
model. A value of 0 means intelligence is not important, while a value of 1
means intelligence is the most important factor.

TJS-type [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tjs-type-1)

number

`Optional` speedPriority [Permalink](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences-speedpriority)

speedPriority?:number

How much to prioritize sampling speed (latency) when selecting a model. A
value of 0 means speed is not important, while a value of 1 means speed is
the most important factor.

TJS-type [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tjs-type-2)

number

### [​](https://modelcontextprotocol.io/specification/draft/schema\#numberschema)  `NumberSchema`

interfaceNumberSchema{

[description](https://modelcontextprotocol.io/specification/draft/schema#)?:string;

[maximum](https://modelcontextprotocol.io/specification/draft/schema#)?:number;

[minimum](https://modelcontextprotocol.io/specification/draft/schema#)?:number;

[title](https://modelcontextprotocol.io/specification/draft/schema#)?:string;

[type](https://modelcontextprotocol.io/specification/draft/schema#):“number”\|“integer”;

}

### [​](https://modelcontextprotocol.io/specification/draft/schema\#primitiveschemadefinition)  `PrimitiveSchemaDefinition`

PrimitiveSchemaDefinition:

\| [StringSchema](https://modelcontextprotocol.io/specification/draft/schema#stringschema)

\| [NumberSchema](https://modelcontextprotocol.io/specification/draft/schema#numberschema)

\| [BooleanSchema](https://modelcontextprotocol.io/specification/draft/schema#booleanschema)

\| [EnumSchema](https://modelcontextprotocol.io/specification/draft/schema#enumschema)

Restricted schema definitions that only allow primitive types
without nested objects or arrays.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#progresstoken)  `ProgressToken`

ProgressToken:string\|number

A progress token, used to associate progress notifications with the original request.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#prompt)  `Prompt`

interfacePrompt{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#prompt-_meta)?:{\[key:string\]:unknown};

[arguments](https://modelcontextprotocol.io/specification/draft/schema#prompt-arguments)?: [PromptArgument](https://modelcontextprotocol.io/specification/draft/schema#promptargument)\[\];

[description](https://modelcontextprotocol.io/specification/draft/schema#prompt-description)?:string;

[name](https://modelcontextprotocol.io/specification/draft/schema#prompt-name):string;

[title](https://modelcontextprotocol.io/specification/draft/schema#prompt-title)?:string;

}

A prompt or prompt template that the server offers.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#prompt-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` arguments [Permalink](https://modelcontextprotocol.io/specification/draft/schema#prompt-arguments)

arguments?: [PromptArgument](https://modelcontextprotocol.io/specification/draft/schema#promptargument)\[\]

A list of arguments to use for templating the prompt.

`Optional` description [Permalink](https://modelcontextprotocol.io/specification/draft/schema#prompt-description)

description?:string

An optional description of what this prompt provides

name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#prompt-name)

name:string

Intended for programmatic or logical use, but used as a display name in past specs or fallback (if title isn’t present).

`Optional` title [Permalink](https://modelcontextprotocol.io/specification/draft/schema#prompt-title)

title?:string

Intended for UI and end-user contexts — optimized to be human-readable and easily understood,
even by those unfamiliar with domain-specific terminology.

If not provided, the name should be used for display (except for Tool,
where `annotations.title` should be given precedence over using `name`,
if present).

### [​](https://modelcontextprotocol.io/specification/draft/schema\#promptargument)  `PromptArgument`

interfacePromptArgument{

[description](https://modelcontextprotocol.io/specification/draft/schema#promptargument-description)?:string;

[name](https://modelcontextprotocol.io/specification/draft/schema#promptargument-name):string;

[required](https://modelcontextprotocol.io/specification/draft/schema#promptargument-required)?:boolean;

[title](https://modelcontextprotocol.io/specification/draft/schema#promptargument-title)?:string;

}

Describes an argument that a prompt can accept.

`Optional` description [Permalink](https://modelcontextprotocol.io/specification/draft/schema#promptargument-description)

description?:string

A human-readable description of the argument.

name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#promptargument-name)

name:string

Intended for programmatic or logical use, but used as a display name in past specs or fallback (if title isn’t present).

`Optional` required [Permalink](https://modelcontextprotocol.io/specification/draft/schema#promptargument-required)

required?:boolean

Whether this argument must be provided.

`Optional` title [Permalink](https://modelcontextprotocol.io/specification/draft/schema#promptargument-title)

title?:string

Intended for UI and end-user contexts — optimized to be human-readable and easily understood,
even by those unfamiliar with domain-specific terminology.

If not provided, the name should be used for display (except for Tool,
where `annotations.title` should be given precedence over using `name`,
if present).

### [​](https://modelcontextprotocol.io/specification/draft/schema\#promptmessage)  `PromptMessage`

interfacePromptMessage{

[content](https://modelcontextprotocol.io/specification/draft/schema#): [ContentBlock](https://modelcontextprotocol.io/specification/draft/schema#contentblock);

[role](https://modelcontextprotocol.io/specification/draft/schema#): [Role](https://modelcontextprotocol.io/specification/draft/schema#role);

}

Describes a message returned as part of a prompt.

This is similar to `SamplingMessage`, but also supports the embedding of
resources from the MCP server.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#promptreference)  `PromptReference`

interfacePromptReference{

[name](https://modelcontextprotocol.io/specification/draft/schema#promptreference-name):string;

[title](https://modelcontextprotocol.io/specification/draft/schema#promptreference-title)?:string;

[type](https://modelcontextprotocol.io/specification/draft/schema#):“ref/prompt”;

}

Identifies a prompt.

name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#promptreference-name)

name:string

Intended for programmatic or logical use, but used as a display name in past specs or fallback (if title isn’t present).

`Optional` title [Permalink](https://modelcontextprotocol.io/specification/draft/schema#promptreference-title)

title?:string

Intended for UI and end-user contexts — optimized to be human-readable and easily understood,
even by those unfamiliar with domain-specific terminology.

If not provided, the name should be used for display (except for Tool,
where `annotations.title` should be given precedence over using `name`,
if present).

### [​](https://modelcontextprotocol.io/specification/draft/schema\#requestid)  `RequestId`

RequestId:string\|number

A uniquely identifying ID for a request in JSON-RPC.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#resource)  `Resource`

interfaceResource{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#resource-_meta)?:{\[key:string\]:unknown};

[annotations](https://modelcontextprotocol.io/specification/draft/schema#resource-annotations)?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations);

[description](https://modelcontextprotocol.io/specification/draft/schema#resource-description)?:string;

[mimeType](https://modelcontextprotocol.io/specification/draft/schema#resource-mimetype)?:string;

[name](https://modelcontextprotocol.io/specification/draft/schema#resource-name):string;

[size](https://modelcontextprotocol.io/specification/draft/schema#resource-size)?:number;

[title](https://modelcontextprotocol.io/specification/draft/schema#resource-title)?:string;

[uri](https://modelcontextprotocol.io/specification/draft/schema#resource-uri):string;

}

A known resource that the server is capable of reading.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resource-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` annotations [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resource-annotations)

annotations?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations)

Optional annotations for the client.

`Optional` description [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resource-description)

description?:string

A description of what this resource represents.

This can be used by clients to improve the LLM’s understanding of available resources. It can be thought of like a “hint” to the model.

`Optional` mimeType [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resource-mimetype)

mimeType?:string

The MIME type of this resource, if known.

name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resource-name)

name:string

Intended for programmatic or logical use, but used as a display name in past specs or fallback (if title isn’t present).

`Optional` size [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resource-size)

size?:number

The size of the raw resource content, in bytes (i.e., before base64 encoding or any tokenization), if known.

This can be used by Hosts to display file sizes and estimate context window usage.

`Optional` title [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resource-title)

title?:string

Intended for UI and end-user contexts — optimized to be human-readable and easily understood,
even by those unfamiliar with domain-specific terminology.

If not provided, the name should be used for display (except for Tool,
where `annotations.title` should be given precedence over using `name`,
if present).

uri [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resource-uri)

uri:string

The URI of this resource.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#resourcecontents)  `ResourceContents`

interfaceResourceContents{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#resourcecontents-_meta)?:{\[key:string\]:unknown};

[mimeType](https://modelcontextprotocol.io/specification/draft/schema#resourcecontents-mimetype)?:string;

[uri](https://modelcontextprotocol.io/specification/draft/schema#resourcecontents-uri):string;

}

The contents of a specific resource or sub-resource.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcecontents-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` mimeType [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcecontents-mimetype)

mimeType?:string

The MIME type of this resource, if known.

uri [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcecontents-uri)

uri:string

The URI of this resource.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#resourcelink)  `ResourceLink`

interfaceResourceLink{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-_meta)?:{\[key:string\]:unknown};

[annotations](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-annotations)?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations);

[description](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-description)?:string;

[mimeType](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-mimetype)?:string;

[name](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-name):string;

[size](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-size)?:number;

[title](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-title)?:string;

[type](https://modelcontextprotocol.io/specification/draft/schema#):“resource\_link”;

[uri](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-uri):string;

}

A resource that the server is capable of reading, included in a prompt or tool call result.

Note: resource links returned by tools are not guaranteed to appear in the results of `resources/list` requests.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` annotations [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-annotations)

annotations?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations)

Optional annotations for the client.

`Optional` description [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-description)

description?:string

A description of what this resource represents.

This can be used by clients to improve the LLM’s understanding of available resources. It can be thought of like a “hint” to the model.

`Optional` mimeType [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-mimetype)

mimeType?:string

The MIME type of this resource, if known.

name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-name)

name:string

Intended for programmatic or logical use, but used as a display name in past specs or fallback (if title isn’t present).

`Optional` size [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-size)

size?:number

The size of the raw resource content, in bytes (i.e., before base64 encoding or any tokenization), if known.

This can be used by Hosts to display file sizes and estimate context window usage.

`Optional` title [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-title)

title?:string

Intended for UI and end-user contexts — optimized to be human-readable and easily understood,
even by those unfamiliar with domain-specific terminology.

If not provided, the name should be used for display (except for Tool,
where `annotations.title` should be given precedence over using `name`,
if present).

uri [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcelink-uri)

uri:string

The URI of this resource.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#resourcetemplate)  `ResourceTemplate`

interfaceResourceTemplate{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-_meta)?:{\[key:string\]:unknown};

[annotations](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-annotations)?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations);

[description](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-description)?:string;

[mimeType](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-mimetype)?:string;

[name](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-name):string;

[title](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-title)?:string;

[uriTemplate](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-uritemplate):string;

}

A template description for resources available on the server.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` annotations [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-annotations)

annotations?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations)

Optional annotations for the client.

`Optional` description [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-description)

description?:string

A description of what this template is for.

This can be used by clients to improve the LLM’s understanding of available resources. It can be thought of like a “hint” to the model.

`Optional` mimeType [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-mimetype)

mimeType?:string

The MIME type for all resources that match this template. This should only be included if all resources matching this template have the same type.

name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-name)

name:string

Intended for programmatic or logical use, but used as a display name in past specs or fallback (if title isn’t present).

`Optional` title [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-title)

title?:string

Intended for UI and end-user contexts — optimized to be human-readable and easily understood,
even by those unfamiliar with domain-specific terminology.

If not provided, the name should be used for display (except for Tool,
where `annotations.title` should be given precedence over using `name`,
if present).

uriTemplate [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate-uritemplate)

uriTemplate:string

A URI template (according to RFC 6570) that can be used to construct resource URIs.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#resourcetemplatereference)  `ResourceTemplateReference`

interfaceResourceTemplateReference{

[type](https://modelcontextprotocol.io/specification/draft/schema#):“ref/resource”;

[uri](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplatereference-uri):string;

}

A reference to a resource or resource template definition.

uri [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplatereference-uri)

uri:string

The URI or URI template of the resource.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#result)  `Result`

interfaceResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#result-_meta)?:{\[key:string\]:unknown};

\[key:string\]:unknown;

}

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#result-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#role)  `Role`

Role:“user”\|“assistant”

The sender or recipient of messages and data in a conversation.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#root)  `Root`

interfaceRoot{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#root-_meta)?:{\[key:string\]:unknown};

[name](https://modelcontextprotocol.io/specification/draft/schema#root-name)?:string;

[uri](https://modelcontextprotocol.io/specification/draft/schema#root-uri):string;

}

Represents a root directory or file that the server can operate on.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#root-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#root-name)

name?:string

An optional name for the root. This can be used to provide a human-readable
identifier for the root, which may be useful for display purposes or for
referencing the root in other parts of the application.

uri [Permalink](https://modelcontextprotocol.io/specification/draft/schema#root-uri)

uri:string

The URI identifying the root. This _must_ start with file:// for now.
This restriction may be relaxed in future versions of the protocol to allow
other URI schemes.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#samplingmessage)  `SamplingMessage`

interfaceSamplingMessage{

[content](https://modelcontextprotocol.io/specification/draft/schema#): [TextContent](https://modelcontextprotocol.io/specification/draft/schema#textcontent) \| [ImageContent](https://modelcontextprotocol.io/specification/draft/schema#imagecontent) \| [AudioContent](https://modelcontextprotocol.io/specification/draft/schema#audiocontent);

[role](https://modelcontextprotocol.io/specification/draft/schema#): [Role](https://modelcontextprotocol.io/specification/draft/schema#role);

}

Describes a message issued to or received from an LLM API.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#servercapabilities)  `ServerCapabilities`

interfaceServerCapabilities{

[completions](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-completions)?:object;

[experimental](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-experimental)?:{\[key:string\]:object};

[logging](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-logging)?:object;

[prompts](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-prompts)?:{listChanged?:boolean};

[resources](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-resources)?:{listChanged?:boolean;subscribe?:boolean};

[tools](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-tools)?:{listChanged?:boolean};

}

Capabilities that a server may support. Known capabilities are defined here, in this schema, but this is not a closed set: any server can define its own, additional capabilities.

`Optional` completions [Permalink](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-completions)

completions?:object

Present if the server supports argument autocompletion suggestions.

`Optional` experimental [Permalink](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-experimental)

experimental?:{\[key:string\]:object}

Experimental, non-standard capabilities that the server supports.

`Optional` logging [Permalink](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-logging)

logging?:object

Present if the server supports sending log messages to the client.

`Optional` prompts [Permalink](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-prompts)

prompts?:{listChanged?:boolean}

Present if the server offers any prompt templates.

Type declaration

- `Optional` listChanged?: boolean



Whether this server supports notifications for changes to the prompt list.


`Optional` resources [Permalink](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-resources)

resources?:{listChanged?:boolean;subscribe?:boolean}

Present if the server offers any resources to read.

Type declaration

- `Optional` listChanged?: boolean



Whether this server supports notifications for changes to the resource list.

- `Optional` subscribe?: boolean



Whether this server supports subscribing to resource updates.


`Optional` tools [Permalink](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities-tools)

tools?:{listChanged?:boolean}

Present if the server offers any tools to call.

Type declaration

- `Optional` listChanged?: boolean



Whether this server supports notifications for changes to the tool list.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#stringschema)  `StringSchema`

interfaceStringSchema{

[description](https://modelcontextprotocol.io/specification/draft/schema#)?:string;

[format](https://modelcontextprotocol.io/specification/draft/schema#)?:“uri”\|“email”\|“date”\|“date-time”;

[maxLength](https://modelcontextprotocol.io/specification/draft/schema#)?:number;

[minLength](https://modelcontextprotocol.io/specification/draft/schema#)?:number;

[title](https://modelcontextprotocol.io/specification/draft/schema#)?:string;

[type](https://modelcontextprotocol.io/specification/draft/schema#):“string”;

}

### [​](https://modelcontextprotocol.io/specification/draft/schema\#textcontent)  `TextContent`

interfaceTextContent{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#textcontent-_meta)?:{\[key:string\]:unknown};

[annotations](https://modelcontextprotocol.io/specification/draft/schema#textcontent-annotations)?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations);

[text](https://modelcontextprotocol.io/specification/draft/schema#textcontent-text):string;

[type](https://modelcontextprotocol.io/specification/draft/schema#):“text”;

}

Text provided to or from an LLM.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#textcontent-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` annotations [Permalink](https://modelcontextprotocol.io/specification/draft/schema#textcontent-annotations)

annotations?: [Annotations](https://modelcontextprotocol.io/specification/draft/schema#annotations)

Optional annotations for the client.

text [Permalink](https://modelcontextprotocol.io/specification/draft/schema#textcontent-text)

text:string

The text content of the message.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#textresourcecontents)  `TextResourceContents`

interfaceTextResourceContents{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents-_meta)?:{\[key:string\]:unknown};

[mimeType](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents-mimetype)?:string;

[text](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents-text):string;

[uri](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents-uri):string;

}

The contents of a specific resource or sub-resource.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` mimeType [Permalink](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents-mimetype)

mimeType?:string

The MIME type of this resource, if known.

text [Permalink](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents-text)

text:string

The text of the item. This must only be set if the item can actually be represented as text (not binary data).

uri [Permalink](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents-uri)

uri:string

The URI of this resource.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#tool)  `Tool`

interfaceTool{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#tool-_meta)?:{\[key:string\]:unknown};

[annotations](https://modelcontextprotocol.io/specification/draft/schema#tool-annotations)?: [ToolAnnotations](https://modelcontextprotocol.io/specification/draft/schema#toolannotations);

[description](https://modelcontextprotocol.io/specification/draft/schema#tool-description)?:string;

[inputSchema](https://modelcontextprotocol.io/specification/draft/schema#tool-inputschema):{

properties?:{\[key:string\]:object};

required?:string\[\];

type:“object”;

};

[name](https://modelcontextprotocol.io/specification/draft/schema#tool-name):string;

[outputSchema](https://modelcontextprotocol.io/specification/draft/schema#tool-outputschema)?:{

properties?:{\[key:string\]:object};

required?:string\[\];

type:“object”;

};

[title](https://modelcontextprotocol.io/specification/draft/schema#tool-title)?:string;

}

Definition for a tool the client can call.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tool-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` annotations [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tool-annotations)

annotations?: [ToolAnnotations](https://modelcontextprotocol.io/specification/draft/schema#toolannotations)

Optional additional tool information.

Display name precedence order is: title, annotations.title, then name.

`Optional` description [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tool-description)

description?:string

A human-readable description of the tool.

This can be used by clients to improve the LLM’s understanding of available tools. It can be thought of like a “hint” to the model.

inputSchema [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tool-inputschema)

inputSchema:{

properties?:{\[key:string\]:object};

required?:string\[\];

type:“object”;

}

A JSON Schema object defining the expected parameters for the tool.

name [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tool-name)

name:string

Intended for programmatic or logical use, but used as a display name in past specs or fallback (if title isn’t present).

`Optional` outputSchema [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tool-outputschema)

outputSchema?:{

properties?:{\[key:string\]:object};

required?:string\[\];

type:“object”;

}

An optional JSON Schema object defining the structure of the tool’s output returned in
the structuredContent field of a CallToolResult.

`Optional` title [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tool-title)

title?:string

Intended for UI and end-user contexts — optimized to be human-readable and easily understood,
even by those unfamiliar with domain-specific terminology.

If not provided, the name should be used for display (except for Tool,
where `annotations.title` should be given precedence over using `name`,
if present).

### [​](https://modelcontextprotocol.io/specification/draft/schema\#toolannotations)  `ToolAnnotations`

interfaceToolAnnotations{

[destructiveHint](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-destructivehint)?:boolean;

[idempotentHint](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-idempotenthint)?:boolean;

[openWorldHint](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-openworldhint)?:boolean;

[readOnlyHint](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-readonlyhint)?:boolean;

[title](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-title)?:string;

}

Additional properties describing a Tool to clients.

NOTE: all properties in ToolAnnotations are **hints**.
They are not guaranteed to provide a faithful description of
tool behavior (including descriptive properties like `title`).

Clients should never make tool use decisions based on ToolAnnotations
received from untrusted servers.

`Optional` destructiveHint [Permalink](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-destructivehint)

destructiveHint?:boolean

If true, the tool may perform destructive updates to its environment.
If false, the tool performs only additive updates.

(This property is meaningful only when `readOnlyHint == false`)

Default: true

`Optional` idempotentHint [Permalink](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-idempotenthint)

idempotentHint?:boolean

If true, calling the tool repeatedly with the same arguments
will have no additional effect on the its environment.

(This property is meaningful only when `readOnlyHint == false`)

Default: false

`Optional` openWorldHint [Permalink](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-openworldhint)

openWorldHint?:boolean

If true, this tool may interact with an “open world” of external
entities. If false, the tool’s domain of interaction is closed.
For example, the world of a web search tool is open, whereas that
of a memory tool is not.

Default: true

`Optional` readOnlyHint [Permalink](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-readonlyhint)

readOnlyHint?:boolean

If true, the tool does not modify its environment.

Default: false

`Optional` title [Permalink](https://modelcontextprotocol.io/specification/draft/schema#toolannotations-title)

title?:string

A human-readable title for the tool.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#completion%2Fcomplete)  `completion/complete`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#completerequest)  `CompleteRequest`

interfaceCompleteRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“completion/complete”;

[params](https://modelcontextprotocol.io/specification/draft/schema#completerequest-params):{

argument:{name:string;value:string};

context?:{arguments?:{\[key:string\]:string}};

ref: [PromptReference](https://modelcontextprotocol.io/specification/draft/schema#promptreference) \| [ResourceTemplateReference](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplatereference);

};

}

A request from the client to the server, to ask for completion options.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#completerequest-params)

params:{

argument:{name:string;value:string};

context?:{arguments?:{\[key:string\]:string}};

ref: [PromptReference](https://modelcontextprotocol.io/specification/draft/schema#promptreference) \| [ResourceTemplateReference](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplatereference);

}

Type declaration

- argument: {name:string;value:string}



The argument’s information





  - name: string



    The name of the argument

  - value: string



    The value of the argument to use for completion matching.
- `Optional` context?: {arguments?:{\[key:string\]:string}}



Additional, optional context for completions





  - `Optional` arguments?: {\[key:string\]:string}



    Previously-resolved variables in a URI template or prompt.
- ref: [PromptReference](https://modelcontextprotocol.io/specification/draft/schema#promptreference) \| [ResourceTemplateReference](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplatereference)


### [​](https://modelcontextprotocol.io/specification/draft/schema\#completeresult)  `CompleteResult`

interfaceCompleteResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#completeresult-_meta)?:{\[key:string\]:unknown};

[completion](https://modelcontextprotocol.io/specification/draft/schema#completeresult-completion):{hasMore?:boolean;total?:number;values:string\[\]};

\[key:string\]:unknown;

}

The server’s response to a completion/complete request

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#completeresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

completion [Permalink](https://modelcontextprotocol.io/specification/draft/schema#completeresult-completion)

completion:{hasMore?:boolean;total?:number;values:string\[\]}

Type declaration

- `Optional` hasMore?: boolean



Indicates whether there are additional completion options beyond those provided in the current response, even if the exact total is unknown.

- `Optional` total?: number



The total number of completion options available. This can exceed the number of values actually sent in the response.

- values: string\[\]



An array of completion values. Must not exceed 100 items.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#elicitation%2Fcreate)  `elicitation/create`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#elicitrequest)  `ElicitRequest`

interfaceElicitRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“elicitation/create”;

[params](https://modelcontextprotocol.io/specification/draft/schema#elicitrequest-params):{

message:string;

requestedSchema:{

properties:{\[key:string\]: [PrimitiveSchemaDefinition](https://modelcontextprotocol.io/specification/draft/schema#primitiveschemadefinition)};

required?:string\[\];

type:“object”;

};

};

}

A request from the server to elicit additional information from the user via the client.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#elicitrequest-params)

params:{

message:string;

requestedSchema:{

properties:{\[key:string\]: [PrimitiveSchemaDefinition](https://modelcontextprotocol.io/specification/draft/schema#primitiveschemadefinition)};

required?:string\[\];

type:“object”;

};

}

Type declaration

- message: string



The message to present to the user.

- requestedSchema: {

properties:{\[key:string\]: [PrimitiveSchemaDefinition](https://modelcontextprotocol.io/specification/draft/schema#primitiveschemadefinition)};

required?:string\[\];

type:“object”;

}



A restricted subset of JSON Schema.
Only top-level properties are allowed, without nesting.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#elicitresult)  `ElicitResult`

interfaceElicitResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#elicitresult-_meta)?:{\[key:string\]:unknown};

[action](https://modelcontextprotocol.io/specification/draft/schema#elicitresult-action):“accept”\|“decline”\|“cancel”;

[content](https://modelcontextprotocol.io/specification/draft/schema#elicitresult-content)?:{\[key:string\]:string\|number\|boolean};

\[key:string\]:unknown;

}

The client’s response to an elicitation request.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#elicitresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

action [Permalink](https://modelcontextprotocol.io/specification/draft/schema#elicitresult-action)

action:“accept”\|“decline”\|“cancel”

The user action in response to the elicitation.

- “accept”: User submitted the form/confirmed the action
- “decline”: User explicitly decline the action
- “cancel”: User dismissed without making an explicit choice

`Optional` content [Permalink](https://modelcontextprotocol.io/specification/draft/schema#elicitresult-content)

content?:{\[key:string\]:string\|number\|boolean}

The submitted form data, only present when action is “accept”.
Contains values matching the requested schema.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#initialize)  `initialize`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#initializerequest)  `InitializeRequest`

interfaceInitializeRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“initialize”;

[params](https://modelcontextprotocol.io/specification/draft/schema#initializerequest-params):{

capabilities: [ClientCapabilities](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities);

clientInfo: [Implementation](https://modelcontextprotocol.io/specification/draft/schema#implementation);

protocolVersion:string;

};

}

This request is sent from the client to the server when it first connects, asking it to begin initialization.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#initializerequest-params)

params:{

capabilities: [ClientCapabilities](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities);

clientInfo: [Implementation](https://modelcontextprotocol.io/specification/draft/schema#implementation);

protocolVersion:string;

}

Type declaration

- capabilities: [ClientCapabilities](https://modelcontextprotocol.io/specification/draft/schema#clientcapabilities)

- clientInfo: [Implementation](https://modelcontextprotocol.io/specification/draft/schema#implementation)

- protocolVersion: string



The latest version of the Model Context Protocol that the client supports. The client MAY decide to support older versions as well.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#initializeresult)  `InitializeResult`

interfaceInitializeResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#initializeresult-_meta)?:{\[key:string\]:unknown};

[capabilities](https://modelcontextprotocol.io/specification/draft/schema#): [ServerCapabilities](https://modelcontextprotocol.io/specification/draft/schema#servercapabilities);

[instructions](https://modelcontextprotocol.io/specification/draft/schema#initializeresult-instructions)?:string;

[protocolVersion](https://modelcontextprotocol.io/specification/draft/schema#initializeresult-protocolversion):string;

[serverInfo](https://modelcontextprotocol.io/specification/draft/schema#): [Implementation](https://modelcontextprotocol.io/specification/draft/schema#implementation);

\[key:string\]:unknown;

}

After receiving an initialize request from the client, the server sends this response.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#initializeresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` instructions [Permalink](https://modelcontextprotocol.io/specification/draft/schema#initializeresult-instructions)

instructions?:string

Instructions describing how to use the server and its features.

This can be used by clients to improve the LLM’s understanding of available tools, resources, etc. It can be thought of like a “hint” to the model. For example, this information MAY be added to the system prompt.

protocolVersion [Permalink](https://modelcontextprotocol.io/specification/draft/schema#initializeresult-protocolversion)

protocolVersion:string

The version of the Model Context Protocol that the server wants to use. This may not match the version that the client requested. If the client cannot support this version, it MUST disconnect.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#logging%2Fsetlevel)  `logging/setLevel`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#setlevelrequest)  `SetLevelRequest`

interfaceSetLevelRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“logging/setLevel”;

[params](https://modelcontextprotocol.io/specification/draft/schema#setlevelrequest-params):{level: [LoggingLevel](https://modelcontextprotocol.io/specification/draft/schema#logginglevel)};

}

A request from the client to the server, to enable or adjust logging.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#setlevelrequest-params)

params:{level: [LoggingLevel](https://modelcontextprotocol.io/specification/draft/schema#logginglevel)}

Type declaration

- level: [LoggingLevel](https://modelcontextprotocol.io/specification/draft/schema#logginglevel)



The level of logging that the client wants to receive from the server. The server should send all logs at this level and higher (i.e., more severe) to the client as notifications/message.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#notifications%2Fcancelled)  `notifications/cancelled`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#cancellednotification)  `CancelledNotification`

interfaceCancelledNotification{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“notifications/cancelled”;

[params](https://modelcontextprotocol.io/specification/draft/schema#cancellednotification-params):{reason?:string;requestId: [RequestId](https://modelcontextprotocol.io/specification/draft/schema#requestid)};

}

This notification can be sent by either side to indicate that it is cancelling a previously-issued request.

The request SHOULD still be in-flight, but due to communication latency, it is always possible that this notification MAY arrive after the request has already finished.

This notification indicates that the result will be unused, so any associated processing SHOULD cease.

A client MUST NOT attempt to cancel its `initialize` request.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#cancellednotification-params)

params:{reason?:string;requestId: [RequestId](https://modelcontextprotocol.io/specification/draft/schema#requestid)}

Type declaration

- `Optional` reason?: string



An optional string describing the reason for the cancellation. This MAY be logged or presented to the user.

- requestId: [RequestId](https://modelcontextprotocol.io/specification/draft/schema#requestid)



The ID of the request to cancel.



This MUST correspond to the ID of a request previously issued in the same direction.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#notifications%2Finitialized)  `notifications/initialized`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#initializednotification)  `InitializedNotification`

interfaceInitializedNotification{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“notifications/initialized”;

[params](https://modelcontextprotocol.io/specification/draft/schema#initializednotification-params)?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown};

}

This notification is sent from the client to the server after initialization has finished.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#initializednotification-params)

params?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown}

Type declaration

- \[key: string\]:unknown

- `Optional`\_meta?: {\[key:string\]:unknown}



See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#notifications%2Fmessage)  `notifications/message`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#loggingmessagenotification)  `LoggingMessageNotification`

interfaceLoggingMessageNotification{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“notifications/message”;

[params](https://modelcontextprotocol.io/specification/draft/schema#loggingmessagenotification-params):{data:unknown;level: [LoggingLevel](https://modelcontextprotocol.io/specification/draft/schema#logginglevel);logger?:string};

}

Notification of a log message passed from server to client. If no logging/setLevel request has been sent from the client, the server MAY decide which messages to send automatically.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#loggingmessagenotification-params)

params:{data:unknown;level: [LoggingLevel](https://modelcontextprotocol.io/specification/draft/schema#logginglevel);logger?:string}

Type declaration

- data: unknown



The data to be logged, such as a string message or an object. Any JSON serializable type is allowed here.

- level: [LoggingLevel](https://modelcontextprotocol.io/specification/draft/schema#logginglevel)



The severity of this log message.

- `Optional` logger?: string



An optional name of the logger issuing this message.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#notifications%2Fprogress)  `notifications/progress`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#progressnotification)  `ProgressNotification`

interfaceProgressNotification{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“notifications/progress”;

[params](https://modelcontextprotocol.io/specification/draft/schema#progressnotification-params):{

message?:string;

progress:number;

progressToken: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);

total?:number;

};

}

An out-of-band notification used to inform the receiver of a progress update for a long-running request.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#progressnotification-params)

params:{

message?:string;

progress:number;

progressToken: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);

total?:number;

}

Type declaration

- `Optional` message?: string



An optional message describing the current progress.

- progress: number



The progress thus far. This should increase every time progress is made, even if the total is unknown.







TJS-type [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tjs-type)



number

- progressToken: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken)



The progress token which was given in the initial request, used to associate this notification with the request that is proceeding.

- `Optional` total?: number



Total number of items to process (or total progress required), if known.







TJS-type [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tjs-type-1)



number


## [​](https://modelcontextprotocol.io/specification/draft/schema\#notifications%2Fprompts%2Flist-changed)  `notifications/prompts/list_changed`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#promptlistchangednotification)  `PromptListChangedNotification`

interfacePromptListChangedNotification{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“notifications/prompts/list\_changed”;

[params](https://modelcontextprotocol.io/specification/draft/schema#promptlistchangednotification-params)?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown};

}

An optional notification from the server to the client, informing it that the list of prompts it offers has changed. This may be issued by servers without any previous subscription from the client.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#promptlistchangednotification-params)

params?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown}

Type declaration

- \[key: string\]:unknown

- `Optional`\_meta?: {\[key:string\]:unknown}



See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#notifications%2Fresources%2Flist-changed)  `notifications/resources/list_changed`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#resourcelistchangednotification)  `ResourceListChangedNotification`

interfaceResourceListChangedNotification{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“notifications/resources/list\_changed”;

[params](https://modelcontextprotocol.io/specification/draft/schema#resourcelistchangednotification-params)?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown};

}

An optional notification from the server to the client, informing it that the list of resources it can read from has changed. This may be issued by servers without any previous subscription from the client.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourcelistchangednotification-params)

params?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown}

Type declaration

- \[key: string\]:unknown

- `Optional`\_meta?: {\[key:string\]:unknown}



See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#notifications%2Fresources%2Fupdated)  `notifications/resources/updated`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#resourceupdatednotification)  `ResourceUpdatedNotification`

interfaceResourceUpdatedNotification{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“notifications/resources/updated”;

[params](https://modelcontextprotocol.io/specification/draft/schema#resourceupdatednotification-params):{uri:string};

}

A notification from the server to the client, informing it that a resource has changed and may need to be read again. This should only be sent if the client previously sent a resources/subscribe request.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#resourceupdatednotification-params)

params:{uri:string}

Type declaration

- uri: string



The URI of the resource that has been updated. This might be a sub-resource of the one that the client actually subscribed to.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#notifications%2Froots%2Flist-changed)  `notifications/roots/list_changed`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#rootslistchangednotification)  `RootsListChangedNotification`

interfaceRootsListChangedNotification{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“notifications/roots/list\_changed”;

[params](https://modelcontextprotocol.io/specification/draft/schema#rootslistchangednotification-params)?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown};

}

A notification from the client to the server, informing it that the list of roots has changed.
This notification should be sent whenever the client adds, removes, or modifies any root.
The server should then request an updated list of roots using the ListRootsRequest.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#rootslistchangednotification-params)

params?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown}

Type declaration

- \[key: string\]:unknown

- `Optional`\_meta?: {\[key:string\]:unknown}



See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#notifications%2Ftools%2Flist-changed)  `notifications/tools/list_changed`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#toollistchangednotification)  `ToolListChangedNotification`

interfaceToolListChangedNotification{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“notifications/tools/list\_changed”;

[params](https://modelcontextprotocol.io/specification/draft/schema#toollistchangednotification-params)?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown};

}

An optional notification from the server to the client, informing it that the list of tools it offers has changed. This may be issued by servers without any previous subscription from the client.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#toollistchangednotification-params)

params?:{\_meta?:{\[key:string\]:unknown};\[key:string\]:unknown}

Type declaration

- \[key: string\]:unknown

- `Optional`\_meta?: {\[key:string\]:unknown}



See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#ping)  `ping`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#pingrequest)  `PingRequest`

interfacePingRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“ping”;

[params](https://modelcontextprotocol.io/specification/draft/schema#pingrequest-params)?:{

\_meta?:{progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);\[key:string\]:unknown};

\[key:string\]:unknown;

};

}

A ping, issued by either the server or the client, to check that the other party is still alive. The receiver must promptly respond, or else may be disconnected.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#pingrequest-params)

params?:{

\_meta?:{progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);\[key:string\]:unknown};

\[key:string\]:unknown;

}

Type declaration

- \[key: string\]:unknown

- `Optional`\_meta?: {progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);\[key:string\]:unknown}



See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.





  - `Optional` progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken)



    If specified, the caller is requesting out-of-band progress notifications for this request (as represented by notifications/progress). The value of this parameter is an opaque token that will be attached to any subsequent notifications. The receiver is not obligated to provide these notifications.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#prompts%2Fget)  `prompts/get`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#getpromptrequest)  `GetPromptRequest`

interfaceGetPromptRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“prompts/get”;

[params](https://modelcontextprotocol.io/specification/draft/schema#getpromptrequest-params):{arguments?:{\[key:string\]:string};name:string};

}

Used by the client to get a prompt provided by the server.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#getpromptrequest-params)

params:{arguments?:{\[key:string\]:string};name:string}

Type declaration

- `Optional` arguments?: {\[key:string\]:string}



Arguments to use for templating the prompt.

- name: string



The name of the prompt or prompt template.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#getpromptresult)  `GetPromptResult`

interfaceGetPromptResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#getpromptresult-_meta)?:{\[key:string\]:unknown};

[description](https://modelcontextprotocol.io/specification/draft/schema#getpromptresult-description)?:string;

[messages](https://modelcontextprotocol.io/specification/draft/schema#): [PromptMessage](https://modelcontextprotocol.io/specification/draft/schema#promptmessage)\[\];

\[key:string\]:unknown;

}

The server’s response to a prompts/get request from the client.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#getpromptresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` description [Permalink](https://modelcontextprotocol.io/specification/draft/schema#getpromptresult-description)

description?:string

An optional description for the prompt.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#prompts%2Flist)  `prompts/list`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#listpromptsrequest)  `ListPromptsRequest`

interfaceListPromptsRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“prompts/list”;

[params](https://modelcontextprotocol.io/specification/draft/schema#listpromptsrequest-params)?:{cursor?:string};

}

Sent from the client to request a list of prompts and prompt templates the server has.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listpromptsrequest-params)

params?:{cursor?:string}

Type declaration

- `Optional` cursor?: string



An opaque token representing the current pagination position.
If provided, the server should return results starting after this cursor.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#listpromptsresult)  `ListPromptsResult`

interfaceListPromptsResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#listpromptsresult-_meta)?:{\[key:string\]:unknown};

[nextCursor](https://modelcontextprotocol.io/specification/draft/schema#listpromptsresult-nextcursor)?:string;

[prompts](https://modelcontextprotocol.io/specification/draft/schema#): [Prompt](https://modelcontextprotocol.io/specification/draft/schema#prompt)\[\];

\[key:string\]:unknown;

}

The server’s response to a prompts/list request from the client.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listpromptsresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` nextCursor [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listpromptsresult-nextcursor)

nextCursor?:string

An opaque token representing the pagination position after the last returned result.
If present, there may be more results available.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#resources%2Flist)  `resources/list`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#listresourcesrequest)  `ListResourcesRequest`

interfaceListResourcesRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“resources/list”;

[params](https://modelcontextprotocol.io/specification/draft/schema#listresourcesrequest-params)?:{cursor?:string};

}

Sent from the client to request a list of resources the server has.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listresourcesrequest-params)

params?:{cursor?:string}

Type declaration

- `Optional` cursor?: string



An opaque token representing the current pagination position.
If provided, the server should return results starting after this cursor.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#listresourcesresult)  `ListResourcesResult`

interfaceListResourcesResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#listresourcesresult-_meta)?:{\[key:string\]:unknown};

[nextCursor](https://modelcontextprotocol.io/specification/draft/schema#listresourcesresult-nextcursor)?:string;

[resources](https://modelcontextprotocol.io/specification/draft/schema#): [Resource](https://modelcontextprotocol.io/specification/draft/schema#resource)\[\];

\[key:string\]:unknown;

}

The server’s response to a resources/list request from the client.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listresourcesresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` nextCursor [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listresourcesresult-nextcursor)

nextCursor?:string

An opaque token representing the pagination position after the last returned result.
If present, there may be more results available.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#resources%2Fread)  `resources/read`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#readresourcerequest)  `ReadResourceRequest`

interfaceReadResourceRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“resources/read”;

[params](https://modelcontextprotocol.io/specification/draft/schema#readresourcerequest-params):{uri:string};

}

Sent from the client to the server, to read a specific resource URI.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#readresourcerequest-params)

params:{uri:string}

Type declaration

- uri: string



The URI of the resource to read. The URI can use any protocol; it is up to the server how to interpret it.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#readresourceresult)  `ReadResourceResult`

interfaceReadResourceResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#readresourceresult-_meta)?:{\[key:string\]:unknown};

[contents](https://modelcontextprotocol.io/specification/draft/schema#): ( [TextResourceContents](https://modelcontextprotocol.io/specification/draft/schema#textresourcecontents) \| [BlobResourceContents](https://modelcontextprotocol.io/specification/draft/schema#blobresourcecontents))\[\];

\[key:string\]:unknown;

}

The server’s response to a resources/read request from the client.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#readresourceresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#resources%2Fsubscribe)  `resources/subscribe`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#subscriberequest)  `SubscribeRequest`

interfaceSubscribeRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“resources/subscribe”;

[params](https://modelcontextprotocol.io/specification/draft/schema#subscriberequest-params):{uri:string};

}

Sent from the client to request resources/updated notifications from the server whenever a particular resource changes.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#subscriberequest-params)

params:{uri:string}

Type declaration

- uri: string



The URI of the resource to subscribe to. The URI can use any protocol; it is up to the server how to interpret it.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#resources%2Ftemplates%2Flist)  `resources/templates/list`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#listresourcetemplatesrequest)  `ListResourceTemplatesRequest`

interfaceListResourceTemplatesRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“resources/templates/list”;

[params](https://modelcontextprotocol.io/specification/draft/schema#listresourcetemplatesrequest-params)?:{cursor?:string};

}

Sent from the client to request a list of resource templates the server has.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listresourcetemplatesrequest-params)

params?:{cursor?:string}

Type declaration

- `Optional` cursor?: string



An opaque token representing the current pagination position.
If provided, the server should return results starting after this cursor.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#listresourcetemplatesresult)  `ListResourceTemplatesResult`

interfaceListResourceTemplatesResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#listresourcetemplatesresult-_meta)?:{\[key:string\]:unknown};

[nextCursor](https://modelcontextprotocol.io/specification/draft/schema#listresourcetemplatesresult-nextcursor)?:string;

[resourceTemplates](https://modelcontextprotocol.io/specification/draft/schema#): [ResourceTemplate](https://modelcontextprotocol.io/specification/draft/schema#resourcetemplate)\[\];

\[key:string\]:unknown;

}

The server’s response to a resources/templates/list request from the client.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listresourcetemplatesresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` nextCursor [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listresourcetemplatesresult-nextcursor)

nextCursor?:string

An opaque token representing the pagination position after the last returned result.
If present, there may be more results available.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#resources%2Funsubscribe)  `resources/unsubscribe`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#unsubscriberequest)  `UnsubscribeRequest`

interfaceUnsubscribeRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“resources/unsubscribe”;

[params](https://modelcontextprotocol.io/specification/draft/schema#unsubscriberequest-params):{uri:string};

}

Sent from the client to request cancellation of resources/updated notifications from the server. This should follow a previous resources/subscribe request.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#unsubscriberequest-params)

params:{uri:string}

Type declaration

- uri: string



The URI of the resource to unsubscribe from.


## [​](https://modelcontextprotocol.io/specification/draft/schema\#roots%2Flist)  `roots/list`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#listrootsrequest)  `ListRootsRequest`

interfaceListRootsRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“roots/list”;

[params](https://modelcontextprotocol.io/specification/draft/schema#listrootsrequest-params)?:{

\_meta?:{progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);\[key:string\]:unknown};

\[key:string\]:unknown;

};

}

Sent from the server to request a list of root URIs from the client. Roots allow
servers to ask for specific directories or files to operate on. A common example
for roots is providing a set of repositories or directories a server should operate
on.

This request is typically used when the server needs to understand the file system
structure or access specific locations that the client has permission to read from.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listrootsrequest-params)

params?:{

\_meta?:{progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);\[key:string\]:unknown};

\[key:string\]:unknown;

}

Type declaration

- \[key: string\]:unknown

- `Optional`\_meta?: {progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken);\[key:string\]:unknown}



See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.





  - `Optional` progressToken?: [ProgressToken](https://modelcontextprotocol.io/specification/draft/schema#progresstoken)



    If specified, the caller is requesting out-of-band progress notifications for this request (as represented by notifications/progress). The value of this parameter is an opaque token that will be attached to any subsequent notifications. The receiver is not obligated to provide these notifications.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#listrootsresult)  `ListRootsResult`

interfaceListRootsResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#listrootsresult-_meta)?:{\[key:string\]:unknown};

[roots](https://modelcontextprotocol.io/specification/draft/schema#): [Root](https://modelcontextprotocol.io/specification/draft/schema#root)\[\];

\[key:string\]:unknown;

}

The client’s response to a roots/list request from the server.
This result contains an array of Root objects, each representing a root directory
or file that the server can operate on.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listrootsresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#sampling%2Fcreatemessage)  `sampling/createMessage`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#createmessagerequest)  `CreateMessageRequest`

interfaceCreateMessageRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“sampling/createMessage”;

[params](https://modelcontextprotocol.io/specification/draft/schema#createmessagerequest-params):{

includeContext?:“none”\|“thisServer”\|“allServers”;

maxTokens:number;

messages: [SamplingMessage](https://modelcontextprotocol.io/specification/draft/schema#samplingmessage)\[\];

metadata?:object;

modelPreferences?: [ModelPreferences](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences);

stopSequences?:string\[\];

systemPrompt?:string;

temperature?:number;

};

}

A request from the server to sample an LLM via the client. The client has full discretion over which model to select. The client should also inform the user before beginning sampling, to allow them to inspect the request (human in the loop) and decide whether to approve it.

params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#createmessagerequest-params)

params:{

includeContext?:“none”\|“thisServer”\|“allServers”;

maxTokens:number;

messages: [SamplingMessage](https://modelcontextprotocol.io/specification/draft/schema#samplingmessage)\[\];

metadata?:object;

modelPreferences?: [ModelPreferences](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences);

stopSequences?:string\[\];

systemPrompt?:string;

temperature?:number;

}

Type declaration

- `Optional` includeContext?: “none”\|“thisServer”\|“allServers”



A request to include context from one or more MCP servers (including the caller), to be attached to the prompt. The client MAY ignore this request.

- maxTokens: number



The maximum number of tokens to sample, as requested by the server. The client MAY choose to sample fewer tokens than requested.

- messages: [SamplingMessage](https://modelcontextprotocol.io/specification/draft/schema#samplingmessage)\[\]

- `Optional` metadata?: object



Optional metadata to pass through to the LLM provider. The format of this metadata is provider-specific.

- `Optional` modelPreferences?: [ModelPreferences](https://modelcontextprotocol.io/specification/draft/schema#modelpreferences)



The server’s preferences for which model to select. The client MAY ignore these preferences.

- `Optional` stopSequences?: string\[\]

- `Optional` systemPrompt?: string



An optional system prompt the server wants to use for sampling. The client MAY modify or omit this prompt.

- `Optional` temperature?: number





TJS-type [Permalink](https://modelcontextprotocol.io/specification/draft/schema#tjs-type)



number


### [​](https://modelcontextprotocol.io/specification/draft/schema\#createmessageresult)  `CreateMessageResult`

interfaceCreateMessageResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#createmessageresult-_meta)?:{\[key:string\]:unknown};

[content](https://modelcontextprotocol.io/specification/draft/schema#): [TextContent](https://modelcontextprotocol.io/specification/draft/schema#textcontent) \| [ImageContent](https://modelcontextprotocol.io/specification/draft/schema#imagecontent) \| [AudioContent](https://modelcontextprotocol.io/specification/draft/schema#audiocontent);

[model](https://modelcontextprotocol.io/specification/draft/schema#createmessageresult-model):string;

[role](https://modelcontextprotocol.io/specification/draft/schema#): [Role](https://modelcontextprotocol.io/specification/draft/schema#role);

[stopReason](https://modelcontextprotocol.io/specification/draft/schema#createmessageresult-stopreason)?:string;

\[key:string\]:unknown;

}

The client’s response to a sampling/create\_message request from the server. The client should inform the user before returning the sampled message, to allow them to inspect the response (human in the loop) and decide whether to allow the server to see it.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#createmessageresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

model [Permalink](https://modelcontextprotocol.io/specification/draft/schema#createmessageresult-model)

model:string

The name of the model that generated the message.

`Optional` stopReason [Permalink](https://modelcontextprotocol.io/specification/draft/schema#createmessageresult-stopreason)

stopReason?:string

The reason why sampling stopped, if known.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#tools%2Fcall)  `tools/call`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#calltoolrequest)  `CallToolRequest`

interfaceCallToolRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“tools/call”;

[params](https://modelcontextprotocol.io/specification/draft/schema#):{arguments?:{\[key:string\]:unknown};name:string};

}

Used by the client to invoke a tool provided by the server.

### [​](https://modelcontextprotocol.io/specification/draft/schema\#calltoolresult)  `CallToolResult`

interfaceCallToolResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#calltoolresult-_meta)?:{\[key:string\]:unknown};

[content](https://modelcontextprotocol.io/specification/draft/schema#calltoolresult-content): [ContentBlock](https://modelcontextprotocol.io/specification/draft/schema#contentblock)\[\];

[isError](https://modelcontextprotocol.io/specification/draft/schema#calltoolresult-iserror)?:boolean;

[structuredContent](https://modelcontextprotocol.io/specification/draft/schema#calltoolresult-structuredcontent)?:{\[key:string\]:unknown};

\[key:string\]:unknown;

}

The server’s response to a tool call.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#calltoolresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

content [Permalink](https://modelcontextprotocol.io/specification/draft/schema#calltoolresult-content)

content: [ContentBlock](https://modelcontextprotocol.io/specification/draft/schema#contentblock)\[\]

A list of content objects that represent the unstructured result of the tool call.

`Optional` isError [Permalink](https://modelcontextprotocol.io/specification/draft/schema#calltoolresult-iserror)

isError?:boolean

Whether the tool call ended in an error.

If not set, this is assumed to be false (the call was successful).

Any errors that originate from the tool SHOULD be reported inside the result
object, with `isError` set to true, _not_ as an MCP protocol-level error
response. Otherwise, the LLM would not be able to see that an error occurred
and self-correct.

However, any errors in _finding_ the tool, an error indicating that the
server does not support tool calls, or any other exceptional conditions,
should be reported as an MCP error response.

`Optional` structuredContent [Permalink](https://modelcontextprotocol.io/specification/draft/schema#calltoolresult-structuredcontent)

structuredContent?:{\[key:string\]:unknown}

An optional JSON object that represents the structured result of the tool call.

## [​](https://modelcontextprotocol.io/specification/draft/schema\#tools%2Flist)  `tools/list`

### [​](https://modelcontextprotocol.io/specification/draft/schema\#listtoolsrequest)  `ListToolsRequest`

interfaceListToolsRequest{

[method](https://modelcontextprotocol.io/specification/draft/schema#):“tools/list”;

[params](https://modelcontextprotocol.io/specification/draft/schema#listtoolsrequest-params)?:{cursor?:string};

}

Sent from the client to request a list of tools the server has.

`Optional` params [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listtoolsrequest-params)

params?:{cursor?:string}

Type declaration

- `Optional` cursor?: string



An opaque token representing the current pagination position.
If provided, the server should return results starting after this cursor.


### [​](https://modelcontextprotocol.io/specification/draft/schema\#listtoolsresult)  `ListToolsResult`

interfaceListToolsResult{

[\_meta](https://modelcontextprotocol.io/specification/draft/schema#listtoolsresult-_meta)?:{\[key:string\]:unknown};

[nextCursor](https://modelcontextprotocol.io/specification/draft/schema#listtoolsresult-nextcursor)?:string;

[tools](https://modelcontextprotocol.io/specification/draft/schema#): [Tool](https://modelcontextprotocol.io/specification/draft/schema#tool)\[\];

\[key:string\]:unknown;

}

The server’s response to a tools/list request from the client.

`Optional`\_meta [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listtoolsresult-_meta)

\_meta?:{\[key:string\]:unknown}

See [General fields: `_meta`](https://modelcontextprotocol.io/specification/draft/basic/index#meta) for notes on `_meta` usage.

`Optional` nextCursor [Permalink](https://modelcontextprotocol.io/specification/draft/schema#listtoolsresult-nextcursor)

nextCursor?:string

An opaque token representing the pagination position after the last returned result.
If present, there may be more results available.

Was this page helpful?

YesNo

[Pagination](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination)

Assistant

Responses are generated using AI and may contain mistakes.