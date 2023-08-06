# Isolation Levels: Comparison between Percona (MySQL) and PostgreSQL

This repository provides an analysis of how different transaction isolation levels work in Percona (a MySQL variant) and PostgreSQL. The comparison is based on the susceptibility of the database systems to various read phenomena under different isolation levels.

## Repository Structure

- **setup**: This directory contains SQL queries to set up the necessary database structures and data for testing the various phenomena.

- **read_phenomenas**: A collection of step-by-step manuals detailing how to reproduce each of the phenomena.


## Results

### MySQL (Percona)

<table>
    <thead>
        <tr>
            <th>Isolation level</th>
            <th>Dirty read</th>
            <th>Lost update</th>
            <th>Non-repeatable read</th>
            <th>Phantom read</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Read uncommitted</td>
            <td>reproducible</td>
            <td>reproducible</td>
            <td>reproducible</td>
            <td>reproducible</td>
        </tr>
        <tr>
            <td>Read committed</td>
            <td>non-reproducible</td>
            <td>reproducible</td>
            <td>reproducible</td>
            <td>reproducible</td>
        </tr>
        <tr>
            <td>Repeatable read</td>
            <td>non-reproducible</td>
            <td>reproducible</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
        </tr>
        <tr>
            <td>Serializable</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
        </tr>
    </tbody>
</table>

### PostgreSQL

<table>
    <thead>
        <tr>
            <th>Isolation level</th>
            <th>Dirty read</th>
            <th>Lost update</th>
            <th>Non-repeatable read</th>
            <th>Phantom read</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Read committed</td>
            <td>non-reproducible</td>
            <td>reproducible</td>
            <td>reproducible</td>
            <td>reproducible</td>
        </tr>
        <tr>
            <td>Repeatable read</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
        </tr>
        <tr>
            <td>Serializable</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
            <td>non-reproducible</td>
        </tr>
    </tbody>
</table>

## Conclusion

The observed results highlight the distinctions in how Percona (MySQL) and PostgreSQL handle transaction isolation. This analysis can serve as a reference for developers and database administrators when choosing an RDBMS or configuring transaction behavior for specific application needs.
