# Contributing to Nest Audio Drop-In PCB

Thank you for your interest in contributing to this project!

## Ways to Contribute

### 1. Hardware Design
- PCB layout improvements
- Component selection optimization
- Thermal management
- EMC improvements

### 2. Measurements and Testing
- Verify measurements from 3D scan
- Test fit prototypes
- Thermal testing
- Audio quality testing

### 3. Documentation
- Fix typos and errors
- Add clarifications
- Translate to other languages
- Create video guides

### 4. Firmware
- ESPHome improvements
- New features
- Bug fixes
- Optimizations

### 5. Community Support
- Answer questions
- Share your build
- Write blog posts
- Create tutorials

## Getting Started

### Prerequisites
- KiCad 9.0+ (for hardware)
- Git (for version control)
- GitHub account
- ESPHome (for firmware)

### Setting Up Development Environment

1. **Fork the Repository**
   ```bash
   # Click "Fork" button on GitHub
   # Or use gh CLI
   gh repo fork owner/nest-audio-pcb
   ```

2. **Clone Your Fork**
   ```bash
   git clone https://github.com/YOUR_USERNAME/nest-audio-pcb.git
   cd nest-audio-pcb
   ```

3. **Add Upstream Remote**
   ```bash
   git remote add upstream https://github.com/OWNER/nest-audio-pcb.git
   ```

4. **Create Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Development Workflow

### Making Changes

1. **Make your changes**
   - Edit files
   - Test thoroughly
   - Update documentation

2. **Commit Changes**
   ```bash
   git add .
   git commit -m "feat: descriptive message"
   ```

3. **Push to Your Fork**
   ```bash
   git push origin feature/your-feature-name
   ```

4. **Create Pull Request**
   - Go to GitHub
   - Click "New Pull Request"
   - Fill in description
   - Link related issues

### Commit Message Format

Use conventional commits:

```
feat: add new mounting hole pattern
docs: update assembly guide
fix: correct BOM component value
refactor: reorganize schematic sheets
test: add thermal testing procedure
chore: update dependencies
```

## Design Guidelines

### PCB Design
- Follow KiCad best practices
- Use standard footprints when possible
- Add test points for debugging
- Document any deviations from reference
- Ensure manufacturability

### Firmware
- Follow ESPHome conventions
- Add comments for complex logic
- Test on actual hardware
- Update example configs

### Documentation
- Use clear, concise language
- Include diagrams where helpful
- Keep formatting consistent
- Update table of contents

## Pull Request Process

1. **Before Submitting**
   - [ ] Tests pass (if applicable)
   - [ ] Documentation updated
   - [ ] No merge conflicts
   - [ ] Commits are clean

2. **PR Description**
   - What changed
   - Why it changed
   - Testing performed
   - Screenshots/logs if relevant

3. **Review Process**
   - Maintainers will review
   - Address feedback
   - May need multiple iterations
   - Be patient and respectful

4. **After Merge**
   - Delete your branch
   - Update your fork
   - Celebrate! 🎉

## Reporting Issues

### Bug Reports

Use this template:

```markdown
**Description**
Clear description of the bug

**To Reproduce**
Steps to reproduce:
1. Step one
2. Step two
3. ...

**Expected Behavior**
What should happen

**Actual Behavior**
What actually happens

**Hardware/Software**
- PCB revision: [e.g., v0.1]
- Firmware version: [e.g., 2025.2.1]
- ESPHome version: [e.g., 2024.12.0]
- Hardware modifications: [if any]

**Logs**
```
Relevant log output
```

**Screenshots**
If applicable

**Additional Context**
Any other information
```

### Feature Requests

Include:
- Clear description
- Use case
- Proposed solution
- Alternatives considered
- Willingness to implement

## Hardware Contributions

### PCB Changes

1. **Schematic Changes**
   - Update relevant .kicad_sch file
   - Update BOM if component changes
   - Run ERC (Electrical Rule Check)
   - Document changes

2. **Layout Changes**
   - Update .kicad_pcb file
   - Run DRC (Design Rule Check)
   - Check manufacturability
   - Update fabrication outputs

3. **Testing Required**
   - Fabricate test PCB
   - Assemble and verify
   - Document results
   - Photos of assembled board

### Measurement Contributions

If you have access to a 3D scanner:
1. Scan components/enclosure
2. Export measurement data
3. Update measurements.md
4. Submit PR with scan files

## Code of Conduct

### Our Standards

- Be respectful and inclusive
- Welcome newcomers
- Accept constructive criticism
- Focus on what's best for the community
- Show empathy

### Unacceptable Behavior

- Harassment or discrimination
- Trolling or insulting comments
- Personal attacks
- Publishing others' private information
- Other unethical conduct

### Enforcement

Violations may result in:
1. Warning
2. Temporary ban
3. Permanent ban

## Licensing

### Hardware
- CERN-OHL-S v2
- All hardware contributions under same license
- Cannot add proprietary restrictions

### Software/Firmware
- Same as parent project
- ESPHome uses MIT license
- Your contributions must be compatible

### Documentation
- CC-BY-SA 4.0 or similar open license
- Allow modifications and sharing
- Attribution required

## Recognition

Contributors will be:
- Listed in README.md
- Mentioned in release notes
- Credited in relevant files
- Thanked publicly!

## Questions?

- Open a discussion on GitHub
- Join community chat
- Email maintainers
- Check existing issues

## Thank You!

Every contribution helps make this project better for everyone. Whether it's:
- Reporting a typo
- Sharing your build
- Submitting a major feature
- Helping others

You're appreciated! ❤️

---

**Happy Contributing!**
