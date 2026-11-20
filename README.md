<!-- ======================================================= -->
<!--             JOHN THE RIPPER MASTERY                    -->
<!-- ======================================================= -->

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:050505,30:10152B,60:00BFFF,100:050505&height=220&section=header&text=JOHN%20THE%20RIPPER&fontSize=48&fontColor=00F7FF&animation=fadeIn&fontAlignY=38&desc=PASSWORD%20AUDITING%20%7C%20HASH%20ANALYSIS%20%7C%20CYBERSECURITY&descSize=13&descAlignY=60&stroke=00F7FF&strokeWidth=1" width="100%" />

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=19&duration=2500&pause=900&color=00F7FF&center=true&vCenter=true&width=750&lines=ACCESSING+PASSWORD+SECURITY+LAB...;INITIALIZING+JOHN+THE+RIPPER...;ANALYZE.+AUDIT.+UNDERSTAND.+SECURE.;FROM+BEGINNER+TO+ADVANCED." />

<br/>

<img src="https://img.shields.io/badge/PROJECT-PASSWORD%20AUDITING-00F7FF?style=for-the-badge&labelColor=050505"/>
<img src="https://img.shields.io/badge/LEVEL-BEGINNER%20%2F%20ADVANCED-8A2BE2?style=for-the-badge&labelColor=050505"/>
<img src="https://img.shields.io/badge/PLATFORM-KALI%20LINUX-00FF88?style=for-the-badge&labelColor=050505"/>

<br/><br/>

**A HANDS-ON JOURNEY INTO PASSWORD SECURITY & HASH AUDITING**

*Breaking down password security, one hash at a time.*

</div>

---

## `01 // SYSTEM OVERVIEW`

> [!IMPORTANT]
> This repository documents my practical journey of mastering **John the Ripper**, from fundamental concepts to advanced password auditing techniques.

John the Ripper is a powerful password security auditing tool used to identify weak passwords through various password-candidate generation and hash-comparison techniques.

### MISSION OBJECTIVES

- Understand password hashing and authentication security.
- Identify different hash formats.
- Master dictionary and wordlist attacks.
- Explore rule-based and incremental attacks.
- Understand mask-based password generation.
- Perform practical password security assessments.
- Analyze results and document security weaknesses.

---

## `02 // CYBERSECURITY VISUALIZATION`

<div align="center">

<img src="https://media.giphy.com/media/3o7qE1YN7aBOFPRw8E/giphy.gif" width="85%" />

<br/><br/>

### THE PASSWORD AUDITING PIPELINE

</div>

```text
             ┌──────────────────────┐
             │  AUTHORIZED HASH     │
             └──────────┬───────────┘
                        │
                        ▼
             ┌──────────────────────┐
             │   HASH IDENTIFICATION│
             └──────────┬───────────┘
                        │
                        ▼
             ┌──────────────────────┐
             │ JOHN THE RIPPER      │
             └──────────┬───────────┘
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
      DICTIONARY       RULES         MASKS
          │             │             │
          └─────────────┼─────────────┘
                        ▼
                HASH COMPARISON
                        │
                 ┌──────┴──────┐
                 ▼             ▼
              MATCH         NO MATCH
                 │             │
                 ▼             ▼
             ANALYSIS      REVIEW
                 │
                 ▼
          SECURITY REPORT
```

---

## `03 // INSTALLATION & ENVIRONMENT`

**Operating Environment:** Kali Linux

```bash
sudo apt update
sudo apt install john -y
```

Verify installation:

```bash
john --version
john --help
john --list=formats
john --list=build-info
```

Prepare RockYou:

```bash
sudo gzip -dk /usr/share/wordlists/rockyou.txt.gz
```

Verify:

```bash
ls -lh /usr/share/wordlists/
```

---

## `04 // BEGINNER LEVEL — CORE OPERATIONS`

### 01. Generate a SHA-256 Hash

```bash
echo -n "hello123" | sha256sum
```

### 02. Prepare a Hash File

```bash
echo "PASTE_HASH_HERE" > hash.txt
```

### 03. Dictionary Attack

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

### 04. Display Recovered Passwords

```bash
john --show hash.txt
```

### 05. Specify Hash Format

```bash
john --format=Raw-SHA256 --wordlist=rockyou.txt hash.txt
```

### 06. Explore Supported Formats

```bash
john --list=formats
```

---

## `05 // INTERMEDIATE LEVEL — ATTACK TECHNIQUES`

<div align="center">

<img src="https://img.shields.io/badge/01-DICTIONARY_ATTACK-00F7FF?style=flat-square"/>
<img src="https://img.shields.io/badge/02-RULE_BASED_ATTACK-8A2BE2?style=flat-square"/>
<img src="https://img.shields.io/badge/03-INCREMENTAL-FF00FF?style=flat-square"/>
<img src="https://img.shields.io/badge/04-MASK_ATTACK-00FF88?style=flat-square"/>

</div>

### Dictionary Attack

```bash
john --wordlist=rockyou.txt hash.txt
```

### Single Crack Mode

```bash
john --single hash.txt
```

### Rule-Based Attack

```bash
john --wordlist=rockyou.txt --rules hash.txt
```

### Incremental Mode

```bash
john --incremental hash.txt
```

### Mask-Based Attack

```bash
john --mask='?d?d?d?d' hash.txt
```

### Session Management

```bash
john --session=my_lab hash.txt
john --status=my_lab
john --restore=my_lab
```

### Mask Character Reference

| Symbol | Character Set |
|:---:|---|
| `?l` | Lowercase letters |
| `?u` | Uppercase letters |
| `?d` | Digits |
| `?s` | Special characters |
| `?a` | All supported character classes |
| `?h` | Lowercase hexadecimal |
| `?H` | Uppercase hexadecimal |

---

## `06 // ADVANCED LEVEL — DEEP DIVE`

**Advanced topics under investigation:**

| Domain | Topics |
|---|---|
| Hash Analysis | MD5, SHA-1, SHA-256, SHA-512 |
| Password Storage | bcrypt, Linux crypt, NTLM |
| Rule Engine | Custom rules, transformations |
| Candidate Generation | Incremental, masks, external mode |
| Performance | Benchmarking, CPU/GPU considerations |
| File Auditing | PDF, ZIP, Office formats |
| Jumbo Edition | Extended formats and capabilities |
| Reporting | Findings, evidence, recommendations |

### Benchmarking

```bash
john --test
```

```bash
john --test --format=Raw-SHA256
```

### Custom Character Set

```bash
john --mask='?1?1?1?1' --1='abc123' hash.txt
```

### Inspect Rules

```bash
john --list=rules
```

---

## `07 // ATTACK WORKFLOW — VISUAL MAP`

```mermaid
flowchart TD
    A(["START"]) --> B["Obtain Authorized Hash"]
    B --> C["Identify Hash Format"]
    C --> D["Prepare Hash File"]
    D --> E{"Select Attack Strategy"}
    E --> F["Dictionary Attack"]
    E --> G["Rule-Based Attack"]
    E --> H["Mask Attack"]
    E --> I["Incremental Attack"]
    F --> J["Analyze Results"]
    G --> J
    H --> J
    I --> J
    J --> K{"Password Recovered?"}
    K -->|YES| L["Document Findings"]
    K -->|NO| M["Review Strategy"]
    M --> E
    L --> N["Security Recommendations"]
    N --> O(["END"])
```

---

## `08 // PRACTICAL LABS & CHALLENGES`

| ID | Practical Exercise | Level |
|:---:|---|:---:|
| 01 | Generate Your First Hash | Beginner |
| 02 | Basic SHA-256 Auditing | Beginner |
| 03 | RockYou Wordlist | Beginner |
| 04 | Hash Format Selection | Beginner |
| 05 | Dictionary Attacks | Intermediate |
| 06 | Single Crack Mode | Intermediate |
| 07 | Rule-Based Attacks | Intermediate |
| 08 | Incremental Attacks | Intermediate |
| 09 | Mask-Based Attacks | Intermediate |
| 10 | Session Restoration | Intermediate |
| 11 | PDF Password Auditing | Advanced |
| 12 | ZIP Password Auditing | Advanced |
| 13 | Custom Rule Development | Advanced |
| 14 | Performance Benchmarking | Advanced |
| 15 | Complete Password Security Audit | Advanced |

---

## `09 // COMMAND CENTER — QUICK REFERENCE`

| Command | Function |
|---|---|
| `john --help` | Help menu |
| `john --version` | Version |
| `john --list=formats` | Supported formats |
| `john --list=rules` | Available rules |
| `john --wordlist=file hash.txt` | Dictionary attack |
| `john --single hash.txt` | Single crack |
| `john --rules hash.txt` | Rule-based attack |
| `john --incremental hash.txt` | Incremental mode |
| `john --mask='?d?d?d?d' hash.txt` | Mask attack |
| `john --show hash.txt` | Display results |
| `john --status` | Status |
| `john --restore` | Restore session |
| `john --test` | Benchmark |

---

## `10 // LEARNING PROGRESS`

| Learning Module | Status |
|---|:---:|
| Installation & Configuration | ⬜ |
| Hash Fundamentals | ⬜ |
| Hash Identification | ⬜ |
| Dictionary Attacks | ⬜ |
| Single Crack Mode | ⬜ |
| Rule-Based Attacks | ⬜ |
| Incremental Mode | ⬜ |
| Mask-Based Attacks | ⬜ |
| Session Management | ⬜ |
| Advanced Hash Formats | ⬜ |
| Custom Rules | ⬜ |
| Jumbo Edition | ⬜ |
| Practical Labs | ⬜ |
| Security Reporting | ⬜ |

---

## `11 // KNOWLEDGE BASE & RESOURCES`

<div align="center">

<a href="https://www.openwall.com/john/">
<img src="https://img.shields.io/badge/OPENWALL-OFFICIAL_WEBSITE-00F7FF?style=for-the-badge&logo=linux&logoColor=white"/>
</a>

<a href="https://github.com/openwall/john">
<img src="https://img.shields.io/badge/GITHUB-SOURCE_CODE-181717?style=for-the-badge&logo=github"/>
</a>

<a href="https://www.kali.org/tools/john/">
<img src="https://img.shields.io/badge/KALI-TOOL_DOCUMENTATION-557C94?style=for-the-badge&logo=kalilinux"/>
</a>

<a href="https://www.openwall.com/john/doc/">
<img src="https://img.shields.io/badge/DOCUMENTATION-LEARN_MORE-8A2BE2?style=for-the-badge"/>
</a>

</div>

---

## `12 // PROJECT AUTHOR`

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=rect&color=0:050505,50:10152B,100:050505&height=100&text=OMJEE%20OJHA&fontSize=38&fontColor=00F7FF&animation=fadeIn&stroke=00F7FF&strokeWidth=1"/>

### CYBERSECURITY ENTHUSIAST

**Learning | Researching | Practicing | Building**

*Focused on cybersecurity, ethical hacking, password security and practical security research.*

<br/>

<img src="https://img.shields.io/badge/CREATED_BY-OMJEE_OJHA-00F7FF?style=for-the-badge&labelColor=050505"/>
<img src="https://img.shields.io/badge/DOMAIN-CYBERSECURITY-8A2BE2?style=for-the-badge&labelColor=050505"/>

<br/><br/>

**"KNOW THE ATTACK. UNDERSTAND THE WEAKNESS. MASTER THE DEFENSE."**

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:050505,40:10152B,80:00BFFF,100:050505&height=120&section=footer"/>

</div>

---

> [!CAUTION]
> **Ethical Use Only:** This repository is intended for educational purposes, password security research, and authorized security auditing. Never use these techniques against systems or password hashes without permission.</div>
