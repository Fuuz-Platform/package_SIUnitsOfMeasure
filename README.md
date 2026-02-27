# SIUnits — Fuuz SI Units of Measure Package

A Fuuz package containing SI (International System of Units) units of measure, unit types, and unit conversions for the Fuuz platform.

## Description

`SIUnits@1.0.0.fuuz` is a Fuuz platform package that provides a complete set of **SI-only** units of measure for use in any Fuuz application. It seeds three core data models — **UnitType**, **Unit**, and **UnitConversion** — giving your application a metric-based measurement system out of the box. This package excludes Imperial units, making it ideal for environments that operate exclusively with the metric system.

## Package Contents

| Data Model | Record Count | Description |
|---|---|---|
| **UnitType** | 17 | SI unit categories plus Amount, Currency, Frequency, and Time |
| **Unit** | 110 | Individual SI units of measure across all unit types |
| **UnitConversion** | 686 | Conversion factors between SI units within the same type |

### Unit Types Included

| Category | Unit Type |
|---|---|
| Area | Area (SI) |
| Density | Density (SI) |
| Energy | Energy (SI) |
| Flow Rate | Flow Rate (SI) |
| Force | Force (SI) |
| Length | Length (SI) |
| Power | Power (SI) |
| Pressure | Pressure (SI) |
| Speed | Speed (SI) |
| Temperature | Temperature (SI) |
| Torque | Torque (SI) |
| Volume | Volume (SI) |
| Weight | Weight (SI) |
| **Standalone** | |
| Amount | Amount |
| Currency | Currency |
| Frequency | Frequency |
| Time | Time |

## When to Use This Package

Use this package when:

- You are setting up a **new Fuuz application** that requires a standardized set of **SI / metric units only**.
- You operate in a region or industry that exclusively uses the **metric system** and do not need Imperial units.
- You want a **lighter-weight alternative** to the full AllUnits package (110 units vs. 164, 686 conversions vs. 1,720).
- You want to **replace the platform's default seed data** with a comprehensive SI unit system.

## How to Import

1. Download the `SIUnits@1.0.0.fuuz` file from this repository.
2. Open your Fuuz application in the platform.
3. **Drag and drop** the `.fuuz` file into the platform UI to import the package.

## Before You Import — Deleting Existing Seed Data

The Fuuz platform seeds default UnitConversion, Unit, and UnitType records into new applications. These **will conflict** with the package import. You must delete the existing seed data first by running the GraphQL mutations provided in [`deleteSeededUnitData.graphql`](deleteSeededUnitData.graphql).

**Mutations must be run in this order** (foreign key dependencies):

1. **`deleteUnitConversion`** — Remove seeded unit conversions first (they reference Units).
2. **`deleteUnit`** — Remove seeded units next (they reference UnitTypes).
3. **`deleteUnitType`** — Remove seeded unit types last.

The `deleteSeededUnitData.graphql` file contains all three mutations pre-built with the default seeded record IDs.

> **Note:** You may need to update the IDs in the mutations or add additional entries depending on your environment. If your application has had units modified, added, or removed since initial setup, the seeded record IDs may differ from the defaults provided.

## Package Metadata

| Field | Value |
|---|---|
| Package Name | `SIUnits` |
| Version | `1.0.0` |
| Spec Version | `2.0.0` |
| Platform Version | `2026.2.1.782` |
| Publisher | `fuuz` |
