# Planned migration from EVA-S1 → Roxan

A small repository to support the planned migration from EVA-S1 to Roxan.

This README contains a quick reference for cloning the project (including
submodules) and a few helpful notes to get started.

## Quick start

Clone the repository and initialize submodules in one step:

		git clone --recurse-submodules <superproject-url>

If you've already cloned the repository, initialize and update submodules with:

		git submodule update --init --recursive

## Notes

- Use the `--recurse-submodules` flag on clone to avoid having to run the
	update command separately.
- If submodules are added or updated upstream, run `git submodule update --remote`
	or re-run the `--recurse-submodules` clone to pick up changes.

## Proxmox configuration

This repository includes a `proxmox.yml` file with a summary of Proxmox hosts,
LXC containers and VMs used in the migration environment. Important: the
`proxmox.yml` file reflects the existing/old EVA-S1 configuration that is the
source environment for the migration to Roxan.

- Hosts
	- host-16 — 192.168.178.77:8006 — notes: Display-Driver-535-247-01-Linux-64-bit

- LXC containers
	- 100: cloudflare — 192.168.178.27 — tags: tunnel — destination: host
	- 101: nextcloud — 192.168.178.28 — tags: tunnel — destination: docker
	- 102: crafty — 192.168.178.29:8443 — tags: tunnel, minecraft — destination: docker
	- 103: playit — 192.168.178.33 — tags: minecraft — destination: docker
	- 104: django - floratech — 192.168.178.35:8000 — tags: tunnel, daphne — destination: docker
	- 105: nvidia — 192.168.178.89:3000 — tags: tunnel, passthrough, ollama, comfy — notes: NVIDIA driver install (no kernel module) — destination: docker
	- 106: invokeai — 192.168.178.161:9090 — tags: tunnel, invoke-ai — notes: NVIDIA driver install (no kernel module) — destination: docker
	- 107: pihole — 192.168.178.34 — tags: tunnel — notes: /admin — destination: docker
	- 108: glance — 192.168.178.35:8080 — tags: tunnel, docker compose — destination: docker

- VMs
	- 200: fedora — 192.168.178.36 — deprecated (-> cloudflare-ssh)

Notes:
- `proxmox.yml` is the canonical config for these items. Use it when scripting
	or automating deployment tasks.
- The `glance/` folder in the repo may contain related assets or services
	(check `glance/` for more project files).

## Next steps

- Review the repository contents and any project-specific documentation.
- If you maintain a fork or local branch, push your changes and open a PR
	against the main branch of the upstream repo.

## Contact / Maintainers

If you need help with the migration plan, reach out to the repository
maintainer or your project lead.

---
_Minimal README created on behalf of the migration plan._