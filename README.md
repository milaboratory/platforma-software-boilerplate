# Platforma Software Boilerplate

This repository serves as a template for managing software packages in the Platforma ecosystem. It provides a standardized structure for organizing and distributing software binaries across different platforms.

## Repository Structure

```
platforma-software-boilerplate/
├── software/                    # Main software directory
│   ├── linux-x64/              # Linux x64 binaries
│   │   └── bin/                # Binary files for Linux x64
│   ├── linux-aarch64/          # Linux ARM64 binaries
│   │   └── bin/                # Binary files for Linux ARM64
│   ├── macosx-x64/             # macOS x64 binaries
│   │   └── bin/                # Binary files for macOS x64
│   ├── macosx-aarch64/         # macOS ARM64 binaries
│   │   └── bin/                # Binary files for macOS ARM64
│   ├── windows-x64/            # Windows x64 binaries
│   │   └── bin/                # Binary files for Windows x64
│   └── package.json            # Software package configuration
├── package.json                # Root package configuration
├── pnpm-workspace.yaml         # PNPM workspace configuration
├── turbo.json                  # Turborepo configuration
├── .gitattributes             # Git attributes for LFS
└── .gitignore                 # Git ignore rules
```

## Initial Setup

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd platforma-software-boilerplate
   ```

2. Initialize Git LFS:
   ```bash
   git lfs install
   ```

3. Ensure `.gitattributes` is properly configured before adding any files:
   ```bash
   # .gitattributes should contain:
   software/linux-x64/** filter=lfs diff=lfs merge=lfs -text
   software/linux-aarch64/** filter=lfs diff=lfs merge=lfs -text
   software/macosx-x64/** filter=lfs diff=lfs merge=lfs -text
   software/macosx-aarch64/** filter=lfs diff=lfs merge=lfs -text
   software/windows-x64/** filter=lfs diff=lfs merge=lfs -text
   ```

4. Commit `.gitattributes` to the repository     

5. Install dependencies:
   ```bash
   pnpm install
   ```

## Managing Software Packages

### Adding New Binaries

1. Make sure `.gitattributes` is properly configured (see Initial Setup step 3)

2. Place your binary files in the appropriate platform directory:
   - For Linux x64: `software/linux-x64/bin/`
   - For Linux ARM64: `software/linux-aarch64/bin/`
   - For macOS x64: `software/macosx-x64/bin/`
   - For macOS ARM64: `software/macosx-aarch64/bin/`
   - For Windows x64: `software/windows-x64/bin/`

3. Update the `software/package.json` with the correct binary names and paths.

4. Build the package:
   ```bash
   pnpm run build
   ```

5. Initialize changesets if not already done:
   ```bash
   pnpm run changeset init
   ```

6. Add and commit your files:
   ```bash
   git add .
   git commit -m "Add binary files"
   ```

## Version Management

This repository uses Changesets for version management:

Create a new changeset:
```bash
pnpm run changeset
```

## License

UNLICENSED - All rights reserved