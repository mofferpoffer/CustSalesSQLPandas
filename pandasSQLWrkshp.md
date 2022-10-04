## Background material pandas/SQL workshop, Kabisa, October 2022

In-memory data analysis platforms typically consist of 4 layers:
1. query API/language.
2. query engine;
3. in-process/in-memory storage;
4. persistent storage;

Often, these layers are tightly integrated. This makes it difficult to partially revamp your platform, for instance by using a new, faster layer for in-memory storage.

Python/pandas is such a tightly integrated platform. It uses:
1. the pandas API for querying,
2. a combination of Python and C (through NumPy) for query execution,
3. C data structures for in-memory storage,
4. CSV, Excel, relational database, pickle, etc. for persistent, external storage.

This tight integration of layers makes pandas inflexible and not future-proof. However, given the huge popularity of pandas, I would be hesitant to advise against learning and using it. It takes time to get proficient in pandas. It is not conceptually difficult, but it has a steep learning curve caused by the huge  amount of class and instance methods and the strange difference between Series and Dataframe objects and their overlapping methods. If you use it on a regular (daily) base, it becomes a very powerful and flexible tool, although it has its limits reagrding speed and storage capacity.

DuckDB is an SQL language API and query engine, for in-memory data analysis. It can be hosted in many languages such as Python, R, Java, C++. It uses PostgreSQL's SQL dialect. In a Python hosted environment, (in-memory) data to analyse can be stored in Arrow tables, pandas tables, or DuckDB's own in-memory storage format. DuckDB can directly imported from externally stored data in CSV, parquet and DuckDB's own external storage format.
In contrast to the eager pandas executions engine, DuckDB's execution engine (as all SQL execution engines) is lazy. That means that user queries in SQL will be optimized by the execution engine and this can lead to substantial execution speed gains.

Resources:
- pandas
  - [Comparison with SQL](https://pandas.pydata.org/docs/getting_started/comparison/comparison_with_sql.html)
  - [Python for Data Analysis](https://wesmckinney.com/book/)
  - [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)
  - [Modern Pandas (Part 2): Method Chaining](https://tomaugspurger.github.io/method-chaining)
- SQL (DuckDB)
  - [DuckDB SQL Introduction](https://duckdb.org/docs/sql/introduction)
  - [iPython SQL Magic extension](https://github.com/catherinedevlin/ipython-sql)
  - [I don't want to learn your garbage query language](https://erikbern.com/2018/08/30/i-dont-want-to-learn-your-garbage-query-language.html)
  - [Python and SQL: Better Together](https://alex-monahan.github.io/2021/08/22/Python_and_SQL_Better_Together.html#an-example-workflow-with-duckdb)
- [Apache Parquet](https://parquet.apache.org/) Data file format for efficient (external) data storage and retrieval.
- [Apache Arrow](https://arrow.apache.org/) In memory data storage format. It aims to be (language) platform independent.
- [Apache Ibis](https://ibis-project.org/) Ibis is a query engine independent query API, inspired by dplyr.
- [Polars](https://www.pola.rs/) Polars is an Apache Arrow based query engine and query API written in Rust.