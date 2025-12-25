# Task C: Single Record Lifecycle Explanation

Example: Meter #123, 10:00 AM, 3000 W

1. **Upload:** CSV file sent to Raw Storage.
2. **Trigger:** New file detected → Transformation process starts.
3. **Cleaning & Validation:** Convert 3000 W → 3.0 kW; check for normal range.
4. **Storage (SQL):** Save for daily report and real-time queries.
5. **Archiving (Parquet):** Convert to compressed format for future analytics.
6. **Success/Failure:** If storage busy, retry automatically. Dead Letter Queue used if failure persists.
