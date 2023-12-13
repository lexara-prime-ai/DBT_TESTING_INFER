
# Run tests downstream of a model 
### (note this will select those tests directly!)
```powershell
# Run tests upstream of a model (indirect selection)
dbt test --select "stg_customers+"
```

```powershell
# Run tests on all models with a particular tag (direct + indirect)
dbt test --select "+stg_customers"
```

```powershell
dbt test --select "tag:my_model_tag"
```
## Test selection(Cautious mode)
It is possible to prevent tests from running if one or more of its parents is unselected (and therefore unbuilt); we call this "cautious" indirect selection.

It will only include tests whose references are each within the selected nodes.

Put another way, it will prevent tests from running if one or more of its parents is unselected.
```powershell
dbt test  --select  "orders" --indirect-selection=cautious  
```

```powershell
dbt build --select  "orders" --indirect-selection=cautious
```
