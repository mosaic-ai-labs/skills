# Social Publishing

Connect social accounts and publish edited videos directly from the API.

Use the live docs as the source of truth for request and response shapes:
[Social API docs](https://docs.mosaic.so/api/social/get-social-connections)

## Procedure

1. **List connections:** `GET /social/connections`
2. **Create a setup flow if needed:** `POST /social/connections`
3. **Run agent** and wait for `outputs[].video_url` in the completed run.
4. **Publish:** `POST /social/post` with `media_urls` pointing to the output and explicit `destinations` when targeting specific connected accounts.
5. **Track:** Poll `GET /social/post/{post_id}`.
6. **Analyze or moderate:** use `GET /social/post/{post_id}/analytics` and `GET /social/post/{post_id}/comments` when needed.

## Supported platforms

Check the docs before acting. Current public platform IDs include `youtube`, `tiktok`, `instagram`, `facebook`, `linkedin`, and `x`.

## Connections

- `GET /social/connections` - [Docs](https://docs.mosaic.so/api/social/get-social-connections)
- `POST /social/connections` - [Docs](https://docs.mosaic.so/api/social/post-social-connections)
- `GET /social/connections/{social_connection_id}` - [Docs](https://docs.mosaic.so/api/social/get-social-connection)
- `DELETE /social/connections/{social_connection_id}` - [Docs](https://docs.mosaic.so/api/social/delete-social-connection)

Use `social_connection_id` from `GET /social/connections` when posting to a specific account. This matters when the organization has multiple connected accounts on the same platform.

## Create a post

Read the current docs before constructing the body:
[Create Social Post](https://docs.mosaic.so/api/social/post-social-post)

Example shape only:

```json
POST /social/post
{
  "post": "Published via Mosaic API",
  "destinations": [
    { "social_connection_id": "SOCIAL_CONNECTION_ID" }
  ],
  "media_urls": ["https://...output_video_url..."]
}
```

If using `platforms`, the API chooses the default active connection for each platform. Use `destinations` for multiple accounts on the same platform.

## Post status and engagement

- `GET /social/post/{post_id}` - [Docs](https://docs.mosaic.so/api/social/get-social-post)
- `GET /social/post/{post_id}/analytics` - [Docs](https://docs.mosaic.so/api/social/get-social-post-analytics)
- `GET /social/post/{post_id}/comments` - [Docs](https://docs.mosaic.so/api/social/get-social-post-comments)

## Update / delete a post

- `PATCH /social/post/{post_id}` - [Docs](https://docs.mosaic.so/api/social/patch-social-post)
- `DELETE /social/post/{post_id}` - [Docs](https://docs.mosaic.so/api/social/delete-social-post)

Read the update docs before mutating posts. Some updates apply only before a scheduled post publishes, and platform-specific fields may require `social_connection_id`.
Do not assume existing posts can edit text, media, or destinations. The current public update surface is rescheduling, approval, comment toggles where supported, and documented `platform_options`; check the docs before sending platform-specific fields.
