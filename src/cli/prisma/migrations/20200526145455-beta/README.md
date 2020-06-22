# Migration `20200526145455-beta`

This migration has been generated by Errorname at 5/26/2020, 2:54:55 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
PRAGMA foreign_keys=OFF;

CREATE TABLE "quaint"."Tenant" (
"id" TEXT NOT NULL  ,"name" TEXT NOT NULL  ,"provider" TEXT NOT NULL  ,"url" TEXT NOT NULL  ,
    PRIMARY KEY ("id"))

CREATE UNIQUE INDEX "quaint"."Tenant.name" ON "Tenant"("name")

PRAGMA "quaint".foreign_key_check;

PRAGMA foreign_keys=ON;
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration ..20200526145455-beta
--- datamodel.dml
+++ datamodel.dml
@@ -1,0 +1,17 @@
+datasource management {
+  provider = "sqlite"
+  url      = env("PMT_MANAGEMENT_URL")
+}
+
+generator client {
+  provider      = "prisma-client-js"
+  output        = env("PMT_OUTPUT")
+  binaryTargets = ["native"]
+}
+
+model Tenant {
+  id       String @default(cuid()) @id
+  name     String @unique
+  provider String
+  url      String
+}
```

