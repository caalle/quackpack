# Example: Phase 1 on a small requirement

## Input

> As a support agent I want to export the customer list to CSV so I can share it with finance.
>
> Notes from the PO: the export should respect the filters on screen. Finance wants it weekly. It must not include card numbers.

## Output

### Decision record

| # | Rule / question | Status | Owner | Source |
|---|---|---|---|---|
| 1 | Export respects the filters currently applied on screen | Confirmed | PO | PO notes |
| 2 | Card numbers are excluded | Confirmed | PO | PO notes |
| 3 | Export contains every matching row, not only the visible page | Assumed | PO | – |
| 4 | Which customer columns go in the file | Unknown | PO, DPO | – |
| 5 | Which roles can export | Unknown | PO, Security | – |
| 6 | Upper limit on export size, or async delivery for large exports | Unknown | PO, tech lead | – |

### Open questions

**High**

- **#5 Who can export?** Owner: PO with Security. Today 120 agents can see the list. If any of them can download 50k customer rows to a laptop, Security has to sign off. Question: "Can every support agent export, or only team leads?"
- **#4 Which columns?** Owner: DPO. The screen shows name, email, phone and last order. Finance may only need customer id and amounts, and every extra PII column raises the bar for #5. Question: "Does finance need name, email and phone, or is customer id plus order data enough?"
- **#3 All rows or the visible page?** Owner: PO. A filter matches 50k rows but the screen shows 20. Exporting 20 makes the feature useless for finance; exporting 50k decides the size question (#6). Question: "When a filter matches 50k rows, does the file contain all 50k?"

**Low**

- **#6 Size limit or async.** Owner: tech lead. Depends on #3. Skip until #3 is answered.

### Enhancements

- Scheduled weekly delivery to finance. "Weekly" in the notes is a cadence, not a requirement for automation; a manual export covers it for now.

### Next step

Take #5, #4 and #3 to Three Amigos. No story until they are answered.
