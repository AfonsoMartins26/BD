# Detective Agency — Relational Database

A relational database for a detective agency. Project for UMinho's Databases 2024/25 class.

See the attached `BD/` folder for file contents and supporting scripts.

Final Grade: 17/20⭐

## Summary

This repository contains SQL, migration scripts, CSV/JSON sample data and small Python parsers used to build and populate a relational database for a detective agency as part of the UMinho Databases course (2024/25).

The project includes:

- Database DDL, indices, views, procedures, users and population scripts (in `BD/sql/`).
- Migration and parser scripts (in `BD/migrations/`), plus sample CSV data and JSON model files used by the parsers.
- Helper scripts and archives (`BD/migrations.zip`, `BD/sql.zip`, `BD/script_maquinavitual.bash`).

## Repository layout (important files)

- `BD/how_to_run_postgress.md` — step-by-step notes to set up and run PostgreSQL for this project.
- `BD/sql/` — ordered SQL files:
  - `belocars_DDL.sql` — schema definition (tables, types)
  - `belocars_Povoamento.sql` — population scripts
  - `belocars_Indices.sql` — indices to add after population
  - `belocars_Procedures.sql` — stored procedures
  - `belocars_Utilizadores.sql` — user/grant setup
  - `belocars_Vistas.sql` — views
  - `belocars_Delete.sql` — cleanup / drop statements
- `BD/migrations/` — contains:
  - `parser_csv.py`, `parser_json.py`, `parser_postgreSQL.py` — small Python scripts to convert and load the `dados/` CSV/JSON data into the database
  - `dados/` — CSV files used to populate tables
  - `model/` — JSON model files describing data shapes
  - `.env` — environment template (if present, do not commit secrets)
- `BD/script_maquinavitual.bash` — helper for VM setup (project-specific).

## Quick start

1. Install PostgreSQL (use `BD/how_to_run_postgress.md` for notes specific to this project).
2. Create a database and a user with appropriate privileges.
3. Run the SQL files from `BD/sql/` in the order shown in the "Repository layout" section. Example sequence:

   1. `belocars_DDL.sql`
   2. `belocars_Utilizadores.sql` (optional: create users and grants)
   3. `belocars_Povoamento.sql`
   4. `belocars_Indices.sql`
   5. `belocars_Procedures.sql`
   6. `belocars_Vistas.sql`

4. (Optional) Use the parsers in `BD/migrations/` to import CSV/JSON data directly into PostgreSQL. Typical steps:

   - Ensure Python 3 is installed.
   - Install any dependencies if needed (e.g., `psycopg2-binary` for direct DB inserts):

     python3 -m pip install psycopg2-binary

   - Configure connection parameters (environment variables or an `.env` file) and run the desired parser, for example:

     python3 BD/migrations/parser_postgreSQL.py

See `BD/migrations/parser_*.py` for usage details and any required arguments.