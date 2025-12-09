# RO-Crate Viewer

A modern, interactive web application for exploring and visualizing Research Object Crates (RO-Crates). Built with Vue 3, TypeScript, and Tailwind CSS, this viewer provides an intuitive interface for navigating complex research data packages and their metadata.

![RO-Crate Viewer](https://img.shields.io/badge/Vue-3-4FC08D?style=flat&logo=vue.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat&logo=typescript&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow.svg) ![License](https://img.shields.io/badge/License-apache-yellow.svg)

## Features

### Core Functionality
- **Dynamic RO-Crate Loading**: Load RO-Crates from URLs or local files
- **Hierarchical File Tree**: Navigate through nested datasets and files with an intuitive tree view
- **Entity Visualization**: View detailed metadata for all entities within the crate
- **Subcrate Support**: Seamlessly explore nested RO-Crates and subcrates
- **Advanced Search**: Query entities using Tantivy query format for precise filtering
- **Type Filtering**: Filter context entities by type (Person, Organization, etc.)

### User Interface
- **Dark/Light Theme**: Toggle between dark and light modes with persistent preferences
- **Responsive Design**: Optimized for desktop and mobile devices
- **Interactive Navigation**: Breadcrumb navigation with history tracking
- **Split-Panel Layout**: Efficient workspace with file tree sidebar and entity details panel
- **Syntax Highlighting**: Beautiful JSON visualization with custom color-coded syntax

### Entity Management
- **Internal Links**: Click-through navigation between related entities
- **External Links**: Direct access to external resources and URLs
- **Linked Entity Details**: View detailed information about referenced entities in overlay dialogs
- **Subcrate Exploration**: Dedicated UI for discovering and navigating nested crates
- **Copy & Download**: Export entity metadata as JSON files

### Technical Features
- **Graph-Based Navigation**: Intelligent tree building from entity relationships
- **Context Awareness**: Separate viewing of file entities and contextual entities
- **Error Handling**: Comprehensive error messages and loading states
- **Type Safety**: Full TypeScript implementation for robust code

## Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn package manager

### Installation

1. Clone the repository:
```bash
git clone https://github.com/arunaengine/ro-crate-explorer.git
cd ro-crate-explorer
```

2. Install dependencies:
```bash
npm install
# or
yarn install
```

3. Start the development server:
```bash
npm run dev
# or
yarn dev
```

4. Open your browser and navigate to `http://localhost:5173` (or the port shown in your terminal)

### Building for Production

```bash
npm run build
# or
yarn build
```

The production-ready files will be in the `dist` directory.

## Usage

### Loading an RO-Crate

1. Enter the URL of an `ro-crate-metadata.json` file in the input field on the home screen
2. Click the "Load" button to fetch and display the crate
3. Alternatively, you can upload a local RO-Crate file(s) (.zip or metadata provided as .json)

### Navigating the Interface

- **File Tree (Left Panel, Top)**: Browse through the hierarchical structure of datasets and files
- **Context Entities (Left Panel, Bottom)**: Explore contextual entities like persons, organizations, and software
- **Entity Details (Right Panel)**: View detailed metadata for the selected entity
- **Breadcrumbs**: Navigate back through your browsing history


### Searching

1. Click the "Search" button in the top navigation
2. Enter a Tantivy query (e.g., `author.name:Smith AND entity_type:Dataset`)
3. Select from the search results to navigate to specific entities

### Exploring Subcrates

When viewing a Dataset entity that contains subcrates:
- Look for "Explore Subcrate" buttons next to subcrate references
- Click to load and navigate into the nested crate
- Use the breadcrumb navigation or back button to return to parent crates

## Architecture

### Component Structure

```
src/
├── components/
│   ├── custom-ui/
│   │   ├── FileTreeItem.vue     # Recursive file tree component
│   │   └── RoCrateEntity.vue    # Entity details display component
│   ├── icons/                   
│   └── ui/                      # Reusable UI components (buttons, cards, etc.)
├── assets/                      # Static assets and images
├── lib/                         
├── router/       
├── views/                      
├── App.vue                      # Main application container
└── main.ts                      # Application entry point
```

### Key Technologies

- **Vue 3**: Progressive JavaScript framework with Composition API
- **TypeScript**: Type-safe development
- **ro-crate**: Official RO-Crate JavaScript library
- **Tailwind CSS**: Utility-first CSS framework
- **shadcn/ui**: High-quality UI components

### State Management

The application uses Vue's reactive system with `ref` and `computed` for state management:
- Entity data and navigation state
- Search and filter states
- UI states (themes, overlays, loading)
- History tracking for breadcrumb navigation

## Configuration

### Indexing Service

The application connects to an [indexing service](https://github.com/arunaengine/rocrate-indexer) for advanced search functionality. Configure the base URL in `App.vue`:

```typescript
const INDEXING_SERVICE_BASE_URL = 'http://localhost:3000';
```

### Default RO-Crate URL

Set a default RO-Crate to load on startup by modifying the `inputUrl` ref in `App.vue`:

```typescript
const inputUrl = ref<string>('https://your-default-crate-url.com/ro-crate-metadata.json')
```

## Contributing

We welcome contributions (following our [Code of Conduct](CODE_OF_CONDUCT.md)) from the community! Here's how you can help:

### Reporting Issues

- Use the GitHub issue tracker to report bugs
- Include detailed steps to reproduce the issue
- Provide information about your environment (browser, OS, etc.)

### Submitting Pull Requests

1. Fork the repository
2. Create a new branch for your feature (`git checkout -b feature/amazing-feature`)
3. Make your changes and commit them (`git commit -m 'Add amazing feature'`)
4. Push to your branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request with a clear description of your changes

### Development Guidelines

- Follow the existing code style and conventions
- Write clear, commented code
- Test your changes thoroughly
- Update documentation as needed
- Keep commits atomic and write meaningful commit messages

### Code Style

- Use TypeScript for all new code
- Follow Vue 3 Composition API best practices
- Use Tailwind CSS utility classes for styling
- Maintain consistent indentation (2 spaces)
- Add JSDoc comments for complex functions

## License

This project is licensed under either of

- Apache License, Version 2.0 (LICENSE-APACHE or http://www.apache.org/licenses/LICENSE-2.0)
- MIT license (LICENSE-MIT or http://opensource.org/licenses/MIT)

at your option. Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in this Service by you, 
as defined in the Apache-2.0 license, shall be dually licensed as above, without any additional terms or conditions.

## Acknowledgments

### Biohackathon Team

This project was developed as part of **Project 3** during the Biohackathon Germany 2025 event. We extend our sincere gratitude to:

- **The Biohackathon organizers** for providing the collaborative environment and resources
- **All Project 3 team members** for their dedication, creativity, and hard work
- **The RO-Crate community** for developing and maintaining the RO-Crate specification

Special thanks to the Biohackathon initiative for fostering innovation in research data management and promoting open science practices. 
This viewer represents a collaborative effort to make research objects more accessible and easier to explore.

### Built With

- [Vue.js](https://vuejs.org/)
- [TypeScript](https://www.typescriptlang.org/) 
- [ro-crate](https://www.npmjs.com/package/ro-crate) 
- [Tailwind CSS](https://tailwindcss.com/)
- [shadcn/ui](https://ui.shadcn.com/)

## Support

For questions, issues, or feature requests:

- Open an issue on GitHub
- Check existing documentation and issues first
- Provide as much context as possible when reporting problems

## Project Status

This project is actively maintained. We welcome community feedback and contributions to improve the RO-Crate viewing experience.

---

**Note**: This viewer is designed to work with RO-Crate metadata files following the [RO-Crate specification](https://www.researchobject.org/ro-crate/). Ensure your crates are compliant with the specification for optimal viewing experience.

Made with ♥ by the Biohackathon Germany 2025 Project 3 Team