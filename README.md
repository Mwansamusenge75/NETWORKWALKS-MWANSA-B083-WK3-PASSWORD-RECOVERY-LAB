# Week 3 — PDF password recovery lab

**Student:** Mwansa Jonathan Musenge  
**Program:** Networkwalks Cybersecurity Internship Batch:083  
**Modules:** W3-PM1, John the Ripper; W3-PM2, Networkwalks browser tools  
**Evidence date:** 25 September 2026

## Submission summary

| Module | Tested file | Method | Recovered password | Result |
| --- | --- | --- | --- | --- |
| W3-PM1 | `samples/module-1-course-pack-PDF1.pdf` | `pdf2john`, John the Ripper, rockyou | `good-luck` | Recovery shown in terminal |
| W3-PM2 | `samples/module-2-attached-PDF1.pdf` | Networkwalks Hash Calculator and Password Cracker | `password1` | Recovery shown in browser; PDF opened |

**File distinction:** The two provided PDFs have similar names but different content and SHA-256 digests. Use the matching sample for each password. The module 1 screenshot of a captured flag is retained as supplied; the course-pack PDF's decrypted page did not produce extractable text in the verification environment.

## Navigate the submission

- [Module 1 PDF report](reports/module-1-john-the-ripper.pdf)
- [Module 2 PDF report](reports/module-2-networkwalks-tools.pdf)
- [Evidence index](evidence/README.md)
- [Integrity manifest](SHA256SUMS.txt)
- `notes/original-terminal-transcript.txt`: supplied terminal notes, retained verbatim.
- `samples/`: both encrypted, instructor-supplied lab PDFs for reproduction. The assignment guides and unrelated optional material are excluded.

## Reproduce locally

For module 1, in a Kali environment with John and its PDF helper installed:

```bash
pdf2john 'samples/module-1-course-pack-PDF1.pdf' > pdf_hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt pdf_hash.txt
john --show --format=PDF pdf_hash.txt
```

If the wordlist exists only as `rockyou.txt.gz`, decompress it first. The exact Kali installation can expose the helper under a different name or path. `pdf_hash.txt` is intentionally excluded because a working hash is derivable from the bundled sample.

For module 2, open [Hash Calculator](https://networkwalks.com/hash-calculator/) and [Password Cracker](https://networkwalks.com/password-cracker/) and follow the [module 2 PDF report](reports/module-2-networkwalks-tools.pdf). The screenshots capture the browser workflow and result.

## Scope and interpretation

This is a controlled recovery exercise on course-provided PDFs. Recovering a wordlist password demonstrates that this particular password was guessable under the selected attack; it does not measure the strength of every PDF or establish a general cracking time. No third-party systems were tested. These are public GitHub materials: the lab passwords and flags are intentionally disclosed for the submission. Review the course's flag submission rules before publishing if flags must remain private.
