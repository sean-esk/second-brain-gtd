# Obsidian Bases Complete Syntax Reference

> Comprehensive reference for `.base` file format, syntax, filters, formulas, and troubleshooting

---

## File Structure

A `.base` file consists of three main sections in YAML format:

```yaml
formulas:
  # Define calculated properties

properties:
  # Configure display settings for columns

views:
  # Define different table views with filters and sorting
```

**CRITICAL:** Bases have NO `source:` or `FROM` section. By default, a base includes **every file in the vault**. You MUST filter to specific folders using the `filters` section in each view.

---

## Formulas Section

Define calculated properties that auto-compute based on other properties.

### Syntax

```yaml
formulas:
  formula-name: 'expression'
```

### Operators

- **Arithmetic:** `+`, `-`, `*`, `/` (MUST be surrounded by spaces!)
- **Comparison:** `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Logical:** `&&` (and), `||` (or), `!` (not)
- **Null coalescing:** `??` (use default if null)

### Examples

```yaml
formulas:
  total-score: '(spread ?? 0) + (excitement ?? 0) + (audience-match ?? 0) + (simplicity ?? 0)'
  price-per-unit: 'price / quantity'
  is-high-priority: 'priority == "high" && status != "done"'
```

### Critical Formula Rules

1. **Arithmetic operators MUST have spaces:**
   - ✅ Correct: `(a + b)`
   - ❌ Wrong: `(a+b)`

2. **Use null coalescing for missing values:**
   - ✅ Correct: `(value ?? 0)`

3. **Text literals in double quotes:**
   - `'status == "active"'`

4. **Entire formula in single quotes:**
   - `'(a + b) * c'`

---

## Properties Section

Configure how properties (columns) are displayed in views.

### Syntax

```yaml
properties:
  property-name:
    displayName: "Column Header"
    width: 120
```

### Built-in File Properties

- `file.name` - File name
- `file.path` - Full file path
- `file.folder` - Folder path
- `file.ctime` - Creation time
- `file.mtime` - Modification time
- `file.cday` - Creation day
- `file.mday` - Modification day

### Examples

```yaml
properties:
  file.name:
    displayName: "Note Title"
    width: 300
  status:
    displayName: "Status"
    width: 100
  total-score:
    displayName: "Score"
    width: 80
```

**Note:** Formula display names go in `properties`, not `formulas` section.

---

## Views Section

Define different ways to display and filter data.

### Syntax

```yaml
views:
  - type: table
    name: "View Name"
    filters:
      # Filter logic (MUST include folder filter!)
    sorts:
      # Sorting rules
```

### Complete View Example

```yaml
views:
  - type: table
    name: "All Items"
    filters:
      and:
        - file.inFolder("01-Projects/YouTube")
    sorts:
      - property: created
        direction: desc

  - type: table
    name: "Active High Priority"
    filters:
      and:
        - file.inFolder("01-Projects")
        - 'status == "active"'
        - 'total-score > 15'
    sorts:
      - property: total-score
        direction: desc
```

---

## Filters: The Most Complex Part

### Filter Structure

Filters must have a root-level `and`, `or`, or `not` wrapper containing filter statements.

### Filter Operators

| Operator | Meaning | Example |
|----------|---------|---------|
| `==` | Equals | `'status == "active"'` |
| `!=` | Not equals | `'status != "done"'` |
| `>` | Greater than | `'score > 10'` |
| `<` | Less than | `'age < 30'` |
| `>=` | Greater or equal | `'priority >= 3'` |
| `<=` | Less or equal | `'rating <= 5'` |

### Filter Functions

| Function | Purpose | Example |
|----------|---------|---------|
| `file.inFolder("path")` | Files in folder (NEW syntax) | `file.inFolder("Projects")` |
| `inFolder(file.file, "path")` | Files in folder (OLD syntax) | `inFolder(file.file, "Projects")` |
| `contains(container, value)` | Check if array contains | `contains(tags, "urgent")` |
| `taggedWith(file.file, tag)` | Check if file has tag | `taggedWith(file.file, "project")` |
| `linksTo(file.file, note)` | Check if links to note | `linksTo(file.file, "MOC")` |

### Simple Filter Examples

```yaml
# Single condition (still needs and wrapper!)
filters:
  and:
    - 'status == "active"'

# Multiple AND conditions
filters:
  and:
    - 'status == "active"'
    - 'priority == "high"'
    - 'score > 10'

# OR conditions
filters:
  or:
    - 'status == "urgent"'
    - 'priority == "high"'

# NOT filter
filters:
  not:
    - 'status == "archived"'
```

### Complex Nested Filters

```yaml
# AND with nested OR
filters:
  and:
    - file.inFolder("01-Projects")
    - 'status != "done"'
    - or:
        - 'priority == "high"'
        - 'priority == "urgent"'

# Multi-level logic
filters:
  or:
    - taggedWith(file.file, "urgent")
    - and:
        - file.inFolder("Projects")
        - 'score > 15'
    - not:
        - 'status == "archived"'
```

### CRITICAL Filter Syntax Rules

1. **String values: double quotes inside single quotes:**
   - ✅ `'status == "active"'`
   - ❌ `"status == 'active'"`
   - ❌ `status == "active"`

2. **Numeric values: no quotes:**
   - ✅ `'score > 10'`
   - ❌ `'score > "10"'`

3. **Property names with hyphens work directly:**
   - ✅ `'idea-status == "active"'`
   - ✅ `'audience-match > 3'`

4. **Root-level filters MUST have and/or/not wrapper:**
   - ✅ Correct:
     ```yaml
     filters:
       and:
         - 'status == "active"'
     ```
   - ❌ Wrong:
     ```yaml
     filters:
       - 'status == "active"'
     ```

5. **ALWAYS include folder filter:**
   ```yaml
   filters:
     and:
       - file.inFolder("your-folder-path")  # REQUIRED!
       - 'other filters here'
   ```

---

## Sorts Section

Define how rows are sorted in a view.

### Syntax

```yaml
sorts:
  - property: property-name
    direction: asc  # or desc
```

### Examples

```yaml
# Single sort
sorts:
  - property: created
    direction: desc

# Multiple sorts (priority order)
sorts:
  - property: priority
    direction: asc
  - property: created
    direction: desc
```

### Sort Directions

- `asc` - Ascending (A-Z, 0-9, oldest to newest)
- `desc` - Descending (Z-A, 9-0, newest to oldest)

---

## Complete Example .base File

```yaml
formulas:
  total-score: '(spread ?? 0) + (excitement ?? 0) + (audience-match ?? 0) + (simplicity ?? 0)'
  is-priority: 'total-score > 15'

properties:
  file.name:
    displayName: "Video Title"
    width: 300
  idea-status:
    displayName: "Status"
    width: 120
  content-type:
    displayName: "Type"
    width: 100
  spread:
    displayName: "Spread"
    width: 80
  excitement:
    displayName: "Excitement"
    width: 100
  audience-match:
    displayName: "Audience"
    width: 100
  simplicity:
    displayName: "Simplicity"
    width: 100
  total-score:
    displayName: "Total"
    width: 80
  created:
    displayName: "Created"
    width: 120

views:
  - type: table
    name: "All Ideas"
    filters:
      and:
        - file.inFolder("00-Inbox/Video-Ideas")
    sorts:
      - property: total-score
        direction: desc

  - type: table
    name: "Unreviewed"
    filters:
      and:
        - file.inFolder("00-Inbox/Video-Ideas")
        - 'idea-status == "unreviewed"'
    sorts:
      - property: created
        direction: desc

  - type: table
    name: "High Priority (15+)"
    filters:
      and:
        - file.inFolder("00-Inbox/Video-Ideas")
        - 'total-score >= 15'
        - 'idea-status != "done"'
    sorts:
      - property: total-score
        direction: desc
```

---

## Common Patterns

### Folder + Multiple Statuses

```yaml
filters:
  and:
    - file.inFolder("01-Projects")
    - or:
        - 'status == "active"'
        - 'status == "pending"'
```

### Exclude Completed

```yaml
filters:
  and:
    - file.inFolder("Projects")
    - not:
        - 'status == "done"'
```

### Score Range

```yaml
filters:
  and:
    - file.inFolder("Ideas")
    - 'score >= 10'
    - 'score <= 20'
```

### Tagged Items

```yaml
filters:
  and:
    - file.inFolder("Notes")
    - taggedWith(file.file, "important")
```

---

## Troubleshooting

### Base Shows All Vault Files

**Symptom:** Every file in vault appears, not just target folder

**Cause:** No folder filter applied

**Fix:** Add to EVERY view:
```yaml
filters:
  and:
    - file.inFolder("your-folder-path")
```

### "Unable to parse filters" Error

**Cause:** Missing and/or/not wrapper

**Fix:**
```yaml
# Wrong
filters:
  - 'status == "active"'

# Correct
filters:
  and:
    - 'status == "active"'
```

### Formula Returns Null

**Cause:** Properties don't exist on some notes

**Fix:** Use null coalescing:
```yaml
formula: '(value1 ?? 0) + (value2 ?? 0)'
```

### Filters Not Working

**Debug checklist:**
- Property names match exactly (case-sensitive)
- String values in double quotes: `'prop == "value"'`
- Numeric values without quotes: `'score > 5'`
- Root filter has and/or/not wrapper
- Folder filter is included

---

## Best Practices

1. **Add folder filters to EVERY view** - Bases include all files by default
2. **Use descriptive view names** - "Active High Priority" not "View 1"
3. **Add sorts to every view** - Makes data scannable
4. **Provide defaults in formulas** - Use `??` operator
5. **Test incrementally** - Add one view at a time
6. **Match property names exactly** - Case-sensitive
7. **Set reasonable column widths** - Better visual layout

---

**Tags:** #obsidian #bases #syntax #reference
