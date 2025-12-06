# ERD-GUIDELINES

MANY-TO-MANY RELATION:  using a separate table callled bridge-table.
<img width="1512" height="982" alt="Screenshot 2025-12-06 at 10 34 52 AM" src="https://github.com/user-attachments/assets/32c8627a-e8a7-483d-a343-22ae3862de13" />

1) ONE-TO-ONE (1:1)
✔ Definition
One record → only ONE related record.
✔ DB Schema Rule
Foreign key is placed on one side
but both sides are unique.
🗂 Example
User ↔ UserProfile
Each user has only ONE profile.
Each profile belongs to only ONE user.
🛠 Schema
Table users {
  id PK
  email
}

Table profiles {
  id PK
  user_id FK UNIQUE  ← VERY IMPORTANT
  bio
}
👉 UNIQUE constraint makes it ONE-to-ONE
Benches:
Foreign key + unique = 1:1
🟩 2) ONE-TO-MANY (1:N)
✔ Definition
One record → many related records.
✔ DB Schema Rule
Foreign key is always on the “many” side
without UNIQUE.
🗂 Example
Category → Many Listings
🛠 Schema
Table category {
  id PK
  name
}

Table listing {
  id PK
  category_id FK  ← NO UNIQUE
  name
}
👉 No UNIQUE → means unlimited listings allowed for one category.
