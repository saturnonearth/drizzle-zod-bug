<script lang="ts">
  import {
    mysqlTable,
    text,
    serial,
  } from 'drizzle-orm/mysql-core';
  import { createInsertSchema } from 'drizzle-zod';
  import { ZodObject } from 'zod';

  export const users = mysqlTable('users', {
    id: serial('id').primaryKey().notNull(),
    name: text('name').notNull(),
  });
  
  const insertSchema = createInsertSchema(users);
  const isZodObject = insertSchema instanceof ZodObject;
</script>

<div>
  Am I a ZOD Object? <span class:error={!isZodObject}>{isZodObject ? 'YES! 🤩' : 'No 😢'}</span>
</div>

<style>
  span {
    color: green;
  }
  .error {
    color: red;
  }
</style>