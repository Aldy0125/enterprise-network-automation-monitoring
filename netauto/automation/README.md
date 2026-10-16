# automation/

Sumber kebenaran dan otomasi konfigurasi. Direncanakan mulai Fase 2.

Rencana isi:
- `inventory/` data perangkat dalam YAML
- `templates/` template konfigurasi Jinja2
- `playbooks/` penyebaran dan backup konfigurasi
- `tests/` pengujian render template tanpa perangkat

Kredensial tidak boleh di-commit; gunakan Ansible Vault atau variabel lingkungan.
