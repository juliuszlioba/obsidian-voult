init supabase:
```shell
npx supabase init
```

start supabase:
```shell
npx supabase start
```

stop supabase:
```shell
npx supabase stop
```

make migration file:
```shell
npx supabase migration new starting-ddl
```

generate typescript types:
```shell
npx supabase gen types typescript --local > ./src/types/database.types.ts
```