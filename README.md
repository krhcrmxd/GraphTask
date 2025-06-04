# React + TypeScript + Vite

This project is a simple educational tool for working with adjacency matrices and graph visualization. It features an interactive 4×4 adjacency matrix editor and a basic graph renderer using SVG.

## Features

-   Input-based 4×4 adjacency matrix:

    -   `0` — no edge
    -   `1` — one directed edge
    -   `2` — two directed edges (in both directions)

-   Simple SVG-based graph visualization
-   Nodes are statically positioned
-   Edges are rendered based on user input
-   State managed using `useState` from React

## Tech Stack

-   **React** (functional components)
-   **TypeScript**
-   **Vite**
-   **Tailwind CSS**
-   **SVG** for graph rendering

## Project Structure

-   The matrix is rendered as a `<table>` with `<input>` fields for edge weights
-   Inputs accept values `0`, `1`, or `2`, and update the internal edge state accordingly
-   A `<svg>` element displays:

    -   **Vertices** as blue circles
    -   **Edges** as arrowed lines pre-defined and selected based on state

## Possible Improvements

-   Dynamic matrix sizing
-   More advanced SVG rendering (curved lines, better layout)
-   Conversion to graph object or adjacency list
-   Add algorithms (e.g., pathfinding, cycle detection)

---
