
# Service Status

## Structure

`ServiceStatus`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `App` | `String` | Optional | - | String getApp() | setApp(String app) |
| `Moto` | `String` | Optional | - | String getMoto() | setMoto(String moto) |
| `Notes` | `Integer` | Optional | - | Integer getNotes() | setNotes(Integer notes) |
| `Users` | `Integer` | Optional | - | Integer getUsers() | setUsers(Integer users) |
| `Time` | `String` | Optional | - | String getTime() | setTime(String time) |
| `Os` | `String` | Optional | - | String getOs() | setOs(String os) |
| `PhpVersion` | `String` | Optional | - | String getPhpVersion() | setPhpVersion(String phpVersion) |
| `Status` | `String` | Required | - | String getStatus() | setStatus(String status) |

## Example (as JSON)

```json
{
  "app": "app2",
  "moto": "moto2",
  "notes": 138,
  "users": 58,
  "time": "time4",
  "status": "status6"
}
```

