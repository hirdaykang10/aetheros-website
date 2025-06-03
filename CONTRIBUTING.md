# Contributing to AetherOS

Thank you for your interest in contributing to AetherOS! Your help is welcome—whether you want to add new features, fix bugs, improve documentation, or suggest ideas.

## How to Contribute

1. **Fork the repository** and create your own branch:
   ```bash
   git checkout -b my-feature-branch
   ```
2. **Make your changes** (see coding standards below).
3. **Test your changes** using the provided scripts:
   - For the AI kernel: `./test_kernel.sh`
   - For the core OS foundation: `./test_core_kernel.sh`
4. **Commit and push** your branch.
5. **Open a Pull Request** on GitHub. Describe your changes and reference any related issues.

## Coding Standards
- Use C++17 for all C++ code.
- Write clear, modular, and well-commented code.
- Keep new features in their own files/directories when possible.
- Document new agents, plugins, or subsystems in the README.

## Adding a New Agent
1. Implement a new agent class in `agents/` inheriting from `BaseAgent`.
2. Register the agent in `kernel/main.cpp` using:
   ```cpp
   orchestrator.registerAgent("AgentName", []() { return std::make_unique<AgentClass>(); });
   ```
3. Rebuild and test with `make` and `./test_kernel.sh`.

## Adding a New Subsystem (Core OS)
1. Add new subsystem files to `core/` (e.g., `scheduler.cpp`, `scheduler.h`).
2. Update `core/main.cpp` to demonstrate and test the new subsystem.
3. Document usage and output in the README.

## Reporting Issues or Requesting Features
- Open an issue on GitHub with a clear description.
- Include steps to reproduce bugs, or a use case for new features.

## Questions or Help
- Open a discussion or issue on GitHub.
- See the README for project structure and build instructions.

Thank you for helping make AetherOS better!
