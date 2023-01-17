Check Franz's made @Model on page

```html
<script type="text/javascript">
  storeData =  { "model": @Html.Raw(Json.Encode(@Model)) };
</script>
```

## Dinamic Links

Produkt:
```razor
@Html.Raw(@StoreModels.ProductLink(XX, "Link Text", "_blank", ""))
```

Produktgroup:
```razor
@Html.Raw(@StoreModels.ProductGroupLink(XX, "Link Text", "_blank", "btn btn-hbr green light"))
```

## Redirect

```razor
Response.Redirect("~/milch");
```