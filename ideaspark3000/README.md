# IdeaSpark 3000 messages

Public device feed: https://arsfeshchenko.github.io/ideaspark3000/message.json

To send a message, append an object to the `messages` array in `message.json`:

```json
{
  "id": 2,
  "date": "2026-11-02",
  "text": "Обіймаю тебе!"
}
```

- Include `date` as `YYYY-MM-DD`, the publication date in Europe/Kyiv. Date metadata can be added to an existing ID without making it unread again.
- IDs must be positive integers in increasing order. Always use a new, larger ID for a new message, including when correcting a previously sent text.
- Keep up to 8 recent messages, in chronological order. Each text may contain up to 384 UTF-8 bytes (roughly 190 Ukrainian letters). The total file must stay under 8192 bytes.
- Commit and push to `master`; wait for GitHub Pages to deploy. The ESP32 checks about every 30 seconds, though Pages deployment and caches can add delay.
- Keep history while the device is offline so it can catch up. Messages removed before it downloads them cannot be recovered. The device retains up to 8 messages and never discards an unread one to admit another; read some mail if the inbox is full.
- The file and repository are public. Do not put Wi-Fi passwords or other secrets here.

Device behavior: mailbox with a protruding envelope and raised flag, without a numeric badge, button opens the oldest unread message as a scrolling line. Further presses open remaining unread messages; after the last one, a press returns to idle. A press from idle replays the latest saved message. Messages and read state survive power loss.

Opened unread letters show an envelope icon and “новий лист”; reopening a read letter shows its publication date. The device does not show a numeric unread badge.
