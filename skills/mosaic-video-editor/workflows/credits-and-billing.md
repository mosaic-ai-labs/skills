# Credits & Billing

## Check balance

```
GET /credits
```

[Docs](https://docs.mosaic.so/api/credits/get-credits)

## Auto top-up settings

Get current settings:

```
GET /credits/settings
```

Enable auto top-ups:

```json
POST /credits/settings
{
  "auto_topup": {
    "enabled": true,
    "threshold": 1000,
    "quantity": 5000
  }
}
```

When credit balance drops below `threshold`, `quantity` credits are purchased automatically at your plan's rate. [Docs](https://docs.mosaic.so/api/credits/get-credits-settings)

## View current plan

```
GET /plan
```

[Docs](https://docs.mosaic.so/api/plan/get-plan)

## List available plans

```
GET /plan/list
```

Available plans: `creator`, `creator_annual`, `professional`, `professional_annual`. [Docs](https://docs.mosaic.so/api/plan/get-plan-list)

## Upgrade plan

```json
POST /plan/upgrade
{ "plan_id": "professional" }
```

[Docs](https://docs.mosaic.so/api/plan/post-plan-upgrade)
