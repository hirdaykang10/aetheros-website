# 🧪 Continuous Integration & Testing

AetherOS uses automated testing and continuous integration (CI) to ensure code quality and reliability.

## CI Pipeline
- Build and test on every commit and pull request
- Run unit, integration, and boot tests
- Check code style and formatting
- Generate and publish test/benchmark reports

## How to Run Tests Locally
```bash
make test
./test_kernel_qemu.sh
./test_core_kernel.sh
```

## Contributing Tests
- Add new tests to the `tests/` directory
- See [CONTRIBUTING.md](CONTRIBUTING.md) for test guidelines

---

> See `.github/workflows/` for CI configuration (GitHub Actions)
