# Ansible Playbooks for STIG Compliance and CMMC 2.0

## Overview

This repository contains a collection of Ansible playbooks designed to automate the implementation of Security Technical Implementation Guides (STIGs) and Cybersecurity Maturity Model Certification (CMMC 2.0) requirements across various systems.

These playbooks help organizations:
- Achieve and maintain compliance with DoD STIG benchmarks
- Meet CMMC 2.0 security requirements across multiple maturity levels
- Automate repetitive hardening tasks
- Enforce consistent security configurations across your infrastructure

## Supported Systems

The playbooks currently support the following platforms:
- Red Hat Enterprise Linux (RHEL) 7/8/9
- Ubuntu 20.04/22.04
- Windows Server 2016/2019/2022
- Cisco IOS devices (limited support)
- VMware ESXi (limited support)

## STIG Compliance

These playbooks implement controls from the following STIG benchmarks:
- Operating System STIGs (RHEL, Ubuntu, Windows)
- Web Server STIGs (Apache, Nginx)
- Database STIGs (MySQL, PostgreSQL)
- Network Device STIGs (Cisco)

Each playbook is tagged with relevant STIG IDs (V-XXXXX) for easy reference to the source requirements.

## CMMC 2.0 Alignment

The playbooks help achieve compliance with CMMC 2.0 practices across all three levels:
- **Level 1 (Foundational)**: Basic cyber hygiene practices
- **Level 2 (Advanced)**: NIST SP 800-171 rev2 controls
- **Level 3 (Expert)**: NIST SP 800-172 controls

Mapping documentation is provided in the `docs/` directory showing how each playbook aligns with specific CMMC practices.

## Getting Started

### Prerequisites
- Ansible 2.9+
- Python 3.6+
- For Windows targets: PowerShell 5.1+ and WinRM configured
- Appropriate privileges on target systems

### Basic Usage

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/ansible-stig-cmmc.git
   cd ansible-stig-cmmc
   ```

2. Review and modify the inventory file to match your environment:
   ```
   vi inventory/hosts
   ```

3. Run a specific playbook (example for RHEL 8 STIG):
   ```
   ansible-playbook -i inventory/hosts playbooks/rhel8-stig-hardening.yml
   ```

4. For CMMC-specific hardening:
   ```
   ansible-playbook -i inventory/hosts playbooks/cmmc-level2-os-hardening.yml
   ```

## Playbook Structure

```
.
├── docs/                   # Documentation and compliance mappings
├── inventory/              # Sample inventory files
├── roles/                  # Ansible roles for specific hardening tasks
├── playbooks/              # Main playbooks organized by system/standard
│   ├── linux/              # Linux-specific playbooks
│   ├── windows/            # Windows-specific playbooks
│   ├── network/            # Network device playbooks
│   └── cmmc/               # CMMC-focused playbooks
├── templates/              # Configuration templates
└── vars/                   # Variable files for different environments
```

## Customization

1. Review and modify variables in `vars/` directory for your environment
2. Adjust tags in playbooks to target specific STIG controls or CMMC practices
3. Use `--skip-tags` to exclude specific controls if needed

## Reporting

Playbooks include optional reporting modules that can:
- Generate STIG checklist files (ckl)
- Create CMMC compliance reports
- Output remediation summaries

Enable reporting by uncommenting relevant sections in the playbooks.

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request with clear documentation of changes

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Disclaimer

These playbooks are provided as-is. Always test in a non-production environment before deployment. Compliance validation should be performed by authorized personnel.
