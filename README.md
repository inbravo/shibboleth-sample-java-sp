# spring-security-saml2-sample
A sample application protected by Spring Security Saml2.


> This project was developed as part of Unicon's [Open Source Support program](https://unicon.net/opensource).
Professional Support / Integration Assistance for this module is available. For more information [visit](https://unicon.net/opensource/cas).


##Configuration

### Context
App is available by default at `https://hostname/sp`.

### SP Metadata
The SP metadata is available under `src\main\resources\metadata`. Deploy the application, and
use the `Metadata Administration` tab to generate new metadata for the SP. Copy the content
and paste them into the `sp-metadata.xml` file.

The newly generated SP metadata needs to be loaded by the IdP, in the `metadata-providers.xml` file.
For example:

```xml
<MetadataProvider id="LocalMetadata"  xsi:type="FilesystemMetadataProvider" 
      metadataFile="/path/to/sp-metadata.xml"/>
```

### IdP Metadata
The IdP metadata is referenced inside the `sp.properties` file. While you are reviewing this file,
also adjust the `host.name` property. This should be pointed to FQDN of the server that hosts the sample
application.

## Build

```bash
gradle build
```

## Deploy
The build script is able to automatically deploy the sample to `$CATALINA_HOME`, via:

```bash
gradle deploy
```

Note that `deploy` will automatically build the sample application as well. 
For this work, you must define the `$CATALINA_HOME` environment variable to point to your
Tomcat installation directory. 

## Test
- The sample application will be available at: `https://hostname/sp`
- The sample application has been tested with Shibboleth IdP 3.1.1
