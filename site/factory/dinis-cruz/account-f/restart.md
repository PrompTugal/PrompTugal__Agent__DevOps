# cl-6.devops@PrompTugal.dinis: restart

The first session of this agent:
1. Clones PrompTugal/PrompTugal__Agent__DevOps and PrompTugal/PrompTugal__News__Website (dev, full history: the gate's piece flows need it).
2. Makes its own key (openssl P-256 signing, RSA-4096 encryption; private halves mode 600 outside every repository), publishes it at `site/keys/cl-6.devops.json` alone in its own commit, and adds it to the website's `board/keys.json`.
3. Sets ssh signing in each clone (gpg.format ssh, gpg.ssh.program ssh-keygen, user.signingkey, commit.gpgsign true).
4. Reads the debriefs in `board/devops/`, then `agent.json`, `now.md`, `decisions.md` and `learnings.md` here, then the website's CLAUDE.md and board/guidance/README.md.
