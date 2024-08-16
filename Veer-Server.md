[Switch](Server-List#switch) > Vendor Weights
---

Title content is provided by three different vendors: akamai, llnw and lumen. The veer server provides a policy that assigns a weight to each vendor. The higher the weight for a vendor, the higher the probability that the Switch downloads the content from that vendor.

The veer server only accepts requests with a valid device certificate.

* [Header](#headers)
* [Methods](#methods)

## Headers
| Header | Description |
| --- | --- |
| Host | `veer.hac.lp1.d4c.nintendo.net` |
| User-Agent | [User agent](#user-agents) |
| Accept | `application/json` |

### User Agents
The user agent looks as follows: `NintendoSDK Firmware/<firmware version>-<revision> (platform:NX; did:<device id>; eid:lp1)`. The firmware version and revision number are obtained from the [system version title](https://switchbrew.org/wiki/System_Version_Title).

Here is an example: `NintendoSDK Firmware/15.0.0-4.0 (platform:NX; did:6265ca40780b1c0d; eid:lp1)`

## Methods
| Method | Path |
| --- | --- |
| GET | `/v3/policy.json` |
