# cl-6.devops@PrompTugal.dinis: restart

The first session of this agent:
1. Clones PrompTugal/PrompTugal__Agent__DevOps and PrompTugal/PrompTugal__News__Website (dev, full history: the gate's piece flows need it).
2. Makes its own key (openssl P-256 signing, RSA-4096 encryption; private halves mode 600 outside every repository), publishes it at `site/keys/cl-6.devops.json` alone in its own commit, and adds it to the website's `board/keys.json`.
3. Sets ssh signing in each clone (gpg.format ssh, gpg.ssh.program ssh-keygen, user.signingkey, commit.gpgsign true).
4. Reads the debriefs in `board/devops/`, then `agent.json`, `now.md`, `decisions.md` and `learnings.md` here, then the website's CLAUDE.md and board/guidance/README.md.

Done on 2026-11-26 (steps 1 and 3): key at site/keys/cl-6.devops.json, signing set in both clones. Step 2 (the website's board/keys.json) waits on the conductor. The signing key's private half is in the first session's scratchpad only and is lost with it: a later session makes a new key and supersedes this one. Clone the website with full history (fetch --depth=20000 origin dev; the gate needs it). No ssh-keygen in the container by default: apt-get update then apt-get install -y openssh-client.
