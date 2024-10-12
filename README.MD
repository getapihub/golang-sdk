# GetAPIHub Golang SDK

This is the official Golang SDK for the [APIHub](https://getapihub.cloud) API. This SDK provides a convenient way to interact with the APIHub API from your Golang application.

## Installation

To install the SDK, run the following command:

```bash
go get github.com/getapihub/sdk-go
```

## Usage

Client initialisation:

```go
package main

import (
	apihubsdk "github.com/getapihub/golang-sdk"
	"github.com/oapi-codegen/oapi-codegen/v2/pkg/securityprovider"
)

func main() {
	xApiKeyAuth, err := securityprovider.NewSecurityProviderApiKey("header", "X-API-Key", "{API_KEY}")
	if err != nil {
		log.Fatal(err)
	}
	client, err := apihubsdk.NewClientWithResponses("https://gateway.getpihub.cloud", apihubsdk.WithRequestEditorFn(xApiKeyAuth.Intercept))
	if err != nil {
		panic(err)
	}

	profile, err = client.GetV2ProfileWithResponse(context.Background(), &apihubsdk.GetV2ProfileParams{
		LiProfileUrl: "https://www.linkedin.com/in/username/",
	})
}
