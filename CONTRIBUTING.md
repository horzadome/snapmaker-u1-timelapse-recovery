# Contributing to Snapmaker U1 Timelapse Recovery Tool

Thank you for your interest in contributing! This tool helps users recover corrupted timelapse videos from their Snapmaker U1 printers.

## How to Contribute

### Reporting Issues

If you encounter a bug or have a feature request:

1. Check existing issues to avoid duplicates
2. Provide clear steps to reproduce the problem
3. Include sample files if possible (non-sensitive data only)
4. Mention your Python version and FFmpeg version (if not running on U1 printer)

### Submitting Changes

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/your-feature`)
3. **Make your changes**
   - Follow PEP 8 style guidelines
   - Keep lines under 79 characters
   - Add comments for complex logic
4. **Test your changes** with actual corrupted MP4 files
5. **Commit with clear messages** (`git commit -m 'Add feature: description'`)
6. **Push to your fork** (`git push origin feature/your-feature`)
7. **Open a Pull Request**

### Code Style

- Follow PEP 8
- Use type hints for function signatures
- Write docstrings for functions and classes
- Keep functions focused and single-purpose

### Testing

Test your changes with:

- Valid MP4 files (should fail gracefully)
- Corrupted Snapmaker U1 timelapse files
- Edge cases (empty files, very large files, etc.)

## Questions?

Open an issue for discussion before working on major changes.

Thank you for helping improve this tool!
