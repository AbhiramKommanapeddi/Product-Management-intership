# Excel Dashboard Implementation Guide

## PM_Assignment_JaruratCare_AbhiramKommanapeddi.xlsx

### Overview Tab Setup

**Key Metrics Section (A1:B6)**

```
Metric                  Value               Formula
Total Tasks            72                  =COUNTA(TaskTracker!A:A)-1
Completed Tasks        18                  =COUNTIF(TaskTracker!H:H,"Completed")
In Progress Tasks      25                  =COUNTIF(TaskTracker!H:H,"In Progress")
Overdue Tasks          5                   =COUNTIFS(TaskTracker!F:F,"<"&TODAY(),TaskTracker!H:H,"<>Completed")
Overall Progress %     42%                 =B3/B2*100
Team Efficiency       78%                 =AVERAGE(FunnelMetrics!G:G)
```

**Project Timeline (A8:F14)**

```
Phase               Milestone                    Deadline    Days Left   Status        Progress
Ideation           Concept Approval             7/17/2025   =DATEDIF(TODAY(),D9,"D")  In Progress   75%
Writing            First Draft Complete         9/11/2025   =DATEDIF(TODAY(),D10,"D") Not Started  0%
Editing            Editorial Review Complete    11/6/2025   =DATEDIF(TODAY(),D11,"D") Not Started  0%
Design             Final Design Approval        11/27/2025  =DATEDIF(TODAY(),D12,"D") Not Started  0%
Publishing         Platform Launch              12/18/2025  =DATEDIF(TODAY(),D13,"D") Not Started  0%
Marketing          Campaign Launch              12/18/2025  =DATEDIF(TODAY(),D14,"D") Planning     15%
```

### Task Tracker Tab Setup

**Column Headers (A1:J1)**
Task ID | Task Name | Team | Assigned To | Start Date | Due Date | Status | Priority | Progress % | Notes

**Sample Data with Formulas**

- Days Overdue: `=IF(AND(F2<TODAY(),G2<>"Completed"),TODAY()-F2,"")`
- Status Color: Use conditional formatting based on Status column
- Priority Urgency: `=IF(H2="Critical","🔴",IF(H2="High","🟡","🟢"))`

**Team Categories:**

- Editorial Team (15 tasks)
- Design Team (8 tasks)
- Marketing Team (10 tasks)
- Cross-functional (5 tasks)

### Funnel Metrics Tab Setup

**Team Handoff Analysis (A1:G8)**

```
Handoff Stage                Tasks In    Tasks Out   Stuck   Avg Days   Efficiency %   Bottleneck Reason
Editorial → Design           15          12          3       14         80%            Resource availability
Design → Marketing           8           6           2       10         75%            Approval delays
Marketing → Publishing       6           4           2       7          67%            Platform requirements
Internal Reviews             12          10          2       5          83%            Stakeholder availability
Cross-team Collaboration     8           6           2       6          75%            Communication gaps
Quality Assurance           10          8           2       4          80%            Standards clarity
Final Approvals             6           4           2       8          67%            Decision timeline
```

**Performance Metrics (A10:F15)**

```
Team        Total Tasks   Completed   In Progress   Overdue   Efficiency %
Editorial   15           8           5             2         =C11/B11*100
Design      8            3           3             2         =C12/B12*100
Marketing   10           4           4             2         =C13/B13*100
Project Mgmt 5           3           1             1         =C14/B14*100
Quality     4            2           2             0         =C15/B15*100
```

### Conditional Formatting Rules

**1. Overdue Tasks (Red Background)**

- Apply to: Task Tracker Tab, columns A:J
- Rule: `=AND($F2<TODAY(),$G2<>"Completed")`
- Format: Red fill, white text

**2. High Priority Tasks (Orange Background)**

- Apply to: Task Tracker Tab, Priority column
- Rule: `=$H2="Critical"`
- Format: Orange fill, black text

**3. Progress Bar Formatting**

- Apply to: Progress % column
- Rule: Data Bars with gradient from Red (0%) to Green (100%)

**4. Team Efficiency Colors**

- Apply to: Funnel Metrics Tab, Efficiency % column
- Rules:
  - <70%: Red background
  - 70-85%: Yellow background
  - > 85%: Green background

### Dashboard Features

**Interactive Elements:**

1. **Dropdown filters** for Team and Status on Task Tracker tab
2. **Date range selector** for timeline analysis
3. **Progress charts** showing completion rates by team
4. **Bottleneck indicator** highlighting stuck tasks

**Charts to Include:**

1. **Gantt Chart** showing project timeline
2. **Pie Chart** showing task distribution by team
3. **Bar Chart** showing team efficiency comparison
4. **Line Graph** tracking progress over time

### Automation Features

**Data Validation:**

- Status dropdown: "Not Started", "In Progress", "Completed", "On Hold"
- Priority dropdown: "Low", "Medium", "High", "Critical"
- Team dropdown: "Editorial", "Design", "Marketing", "Project Management"

**Calculated Fields:**

- Auto-calculate days remaining
- Auto-flag overdue items
- Auto-update completion percentages
- Auto-generate efficiency metrics

### Instructions for Use

1. **Daily Updates**: Update task status and progress percentages
2. **Weekly Reviews**: Check funnel metrics and bottleneck analysis
3. **Monthly Reports**: Generate summary reports from Overview tab
4. **Stakeholder Updates**: Use Overview tab for executive summaries

This Excel dashboard provides comprehensive project tracking with real-time metrics, visual indicators, and automated calculations to ensure the book publishing project stays on track while supporting Jarurat Care's mission of cancer support funding.
