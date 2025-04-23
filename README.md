# 🚀 Custom API Migration Client for WSO2 API Manager

This tool is designed to **automatically re-publish all APIs** currently in the `PUBLISHED` state after a WSO2 API Manager migration.  
Supports **multi-tenancy**—run the client **per tenant** for tenant-specific API redeployment.

✅ **Tested on**: `WSO2 API Manager 3.2.1`  
💡 *Compatible with newer versions by updating* `carbon.apimgt.version` *in* `pom.xml`.

---

## 📦 Prerequisites

Before running the migration client, ensure the following files are present in the **same directory**:

- `Migration-Client-1.0-SNAPSHOT-jar-with-dependencies.jar`
- `client-truststore.jks` (copy from `<APIM_HOME>/repository/resources/security`)
- `config.properties` (configure as shown below)

---

## ⚙️ Configuration: `config.properties`

```properties
# Truststore Configuration
TRUSTSTORE.PATH = client-truststore.jks
TRUSTSTORE.PASSWORD = <trust-store_password>

# Resident Key Manager Endpoints
RESIDENTKM.DCR.URL = https://<KM_HOST>:<PORT>/client-registration/v0.17/register
RESIDENTKM.TOKEN.URL = https://<KM_HOST>:<PORT>/oauth2/token
RESIDENTKM.USERNAME = <TENANT_ADMIN_USERNAME>
RESIDENTKM.PASSWORD = <TENANT_ADMIN_PASSWORD>

# Publisher REST API Endpoint
PUBLISHER.REST.URL = https://<PUBLISHER_HOST>:<PORT>/api/am/publisher/v1/apis

# Migration Parameters
RUN.API.REDEPLOY = true
API.REDEPLOY.THREAD.SLEEP.TIME = <THREAD_SLEEP_TIME_IN_MS>
