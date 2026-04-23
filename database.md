# DATABASE RULES (STRICT / DB-HEAVY)

1. PRINCIPLES:
   - Minimum cost (compute/memory)
   - Minimum I/O operations
   - Minimum lock contention

2. MANDATORY EVALUATION:
   - Cardinality & selectivity
   - Proper index usage
   - Join order & optimization strategies
   - Execution Impact: CPU, Memory, Disk, Network

3. ANTI-PATTERNS TO AVOID:
   - N+1 query problems
   - Queries inside loops
   - Unnecessary temporary tables
   - Layered/cascading writes

4. PREFERRED STRATEGIES:
   - Use `upsert` / `merge` when applicable
   - Employ batch processing for bulk operations
   - Utilize query rewriting for performance
   - Choose strategies contextually, not as rigid templates

5. SCALABILITY:
   - Must be safe for large datasets
   - Ensure minimal database locking
   - Must remain performant as data volume grows

6. FINAL VERIFICATION:
   - Provide a brief explanation regarding: efficiency reasons, trade-offs made, and risks avoided.

7. DEVELOPMENT SCHEMA MANAGEMENT:
   - **NO ALTER DURING DEVELOPMENT:** To maintain a clean and deterministic schema, using `ALTER TABLE` during the development phase is STRICTLY FORBIDDEN.
   - **RESET-FIRST APPROACH:** If the database structure needs to change, the existing database must be **RESET** (Dropped and Recreated) with the new schema.
   - **USER CONFIRMATION:** AI Agents MUST NOT perform a database reset automatically. Always ask the user to execute the reset/seed command (e.g., `npm run db:reset`) after a schema change is implemented in the source code.