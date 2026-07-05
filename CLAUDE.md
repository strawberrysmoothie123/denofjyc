# Daily Market Report Routine — Notification Policy

When this repo's scheduled routine finishes generating a daily market report
(US `market-report-*.md` or KR `kr-market-report-*.md`), always send a
`PushNotification` so the report reaches the user by email without them
having to open Claude or GitHub.

- Lead with one sentence giving the market's overall direction/close (this
  becomes the phone banner).
- After that, include a full comprehensive summary in the `<routine_summary>`
  body — not just a one-liner. Cover, in compact prose:
  - Section 1 one-paragraph summary (verbatim or near-verbatim)
  - Section 3 index levels: close, change (pts/%) for S&P 500, Nasdaq, Dow,
    Russell 2000, VIX
  - Key drivers/news from Section 2 (top 2-3 items)
  - Section 4/5 headline numbers (10yr yield, DXY) if notably moved
  - Section 6 tomorrow's key catalysts
  - The branch name / file name where the full report was committed, so the
    user can find it on GitHub.
- Do not skip the notification just because the report is "routine" — the
  point of this notification is to deliver the report itself, not just to
  flag anomalies. Only skip sending if there was genuinely no new report to
  generate (e.g., US market holiday, no new session).
- Note: `PushNotification` cannot attach files or render markdown tables —
  it is a text-only summary. Do not attempt to paste the entire raw `.md`
  file (with tables) into it; give the reader everything they need to
  understand the day's market without opening the file.
