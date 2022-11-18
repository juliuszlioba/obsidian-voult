## Model check
Check Franz's made @Model on page

```html
<script type="text/javascript">
  storeData =  { "model": @Html.Raw(Json.Encode(@Model)) };
</script>
```

## Dinamic Links

```html
@Html.Raw(@StoreModels.ProductLink(XX, "Link Text", "_blank", ""))
@Html.Raw(@StoreModels.ProductGroupLink(XX, "Link Text", "_blank", "btn btn-hbr green light"))
```

## Redirect

```html
Response.Redirect("~/milch");
@{ Response.Redirect("~/milch");}
```