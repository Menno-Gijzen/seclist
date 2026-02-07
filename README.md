![Menno Gijzen Cyber Security](https://raw.githubusercontent.com/Menno-Gijzen/images/main/menno_gijzen_cyber_security_transparent.png)

# SecList

A curated collection of reconnaissance, fuzzing, payload and credential data that fuels offensive security tooling. The lists are organized by the stage of an assessment and by the format expected by tools such as `ffuf`, `wfuzz`, `dirb`, Burp Suite, hash crackers and custom scripts. Subdirectories often bundle their own README detailing sources or usage notes, so start there when you need extra context.

## Repository layout at a glance

- `ai/` – experiments that benchmark how large language models behave with security prompts. `llm_testing` contains folders such as `bias_testing`, `data_Leakage`, `divergence_attack`, `ethical_and_Safety_boundaries` and `memory_Recall_Testing` that capture prompts/responses for analysis rather than production tooling.
- `Discovery/` – wordlists for enumeration, ranging from DNS/FQDN and infrastructure names to files, web-content paths and application-specific keywords. Expect subfolders like `Web-Content`, `File-System`, `Infrastructure`, `SNMP`, `Variables` and `Mainframe`. Nested datasets such as `trickest-robots-disallowed-wordlists` or `BurpSuite-ParamMiner` live under `Web-Content`.
- `Dutch/` – high-volume Dutch dictionaries and password lists useful when targeting Dutch-speaking environments.
- `Fuzzing/` – payloads organized by the validation they affect: `403`, form `Amounts`, DB engine names, `Dates` (2019–2025), various `User-Agents`, `LFI`, `XSS` polyglots and other fuzz strings.
- `Miscellaneous/` – general-purpose datasets that complement the focused directories, including top domains (`top-domains-alexa.csv.zip`, `top-domains-majestic.csv.zip`), wordlists (`lang-english.txt`, `lang-german.txt`, `wordlist-skipfish.fuzz.txt`), DNS resolvers, city names, control characters and themed subfolders such as `Security-Question-Answers`.
- `Pattern-Matching/` – strings for identifying dangerous patterns, logs or PHP source code. Files such as `dangerous-functions-angular.txt`, `errors.txt`, `php-magic-hashes.txt`, `repository scan` hints and `pcap-strings` support triage/alert tuning.
- `Passwords/` – password dumps grouped into `Books`, `Common-Credentials`, `Default-Credentials`, `Leaked-Databases`, `Malware`, `Permutations`, `PHP-Hashes`, `WiFi-WPA` and more. Large lists reside inside `withcount`, compressed archives and `SCRABBLE-hackerhouse.tgz` while `scraped-JWT-secrets.txt` (from wallarm/jwt-secrets) provides a modern target set. Review the directory README for instructions on huge files and external mirrors.
- `Payloads/` – DoS/anti-virus test payloads, zip bombs and obfuscated filenames. Notable assets include the `Payloads/README.md` saga entries (`lottapixel`, `uber.gif`, `EICAR`, `xssproject`, `PHPInfo.zip` plus helper scripts and GIF/SWF PoCs).
- `Pattern-Matching/Source-Code-(PHP)` – (if present) more focused PHP source snippets for grep-based scanning.
- `Usernames/` – default usernames, honeypot captures, MSI usernames and massive lists such as `xato-net-10-million-usernames.txt`. This directory also holds a README documenting its scope.
- `Web-Shells/` – example shells and payloads for frameworks such as PHP, JSP, Magento, WordPress, Vtiger, CFM and the laudanum collection.

## Getting started

1. Find the list you need with `rg --files | rg NAME` or `findstr`/`ls`. The subfolder READMEs often flag how the list was sourced or any special handling (e.g., `Payloads/PHPInfo.zip` cannot be unzipped on Windows; use WSL or `bsdtar`).
2. Combine files with `cat`, `sort -u` and redirect them into tool-specific input, e.g. `cat Discovery/Web-Content/trickest-robots-disallowed-wordlists/* >> custom.txt`.
3. Feed the flattened list to your tool of choice (`ffuf -w custom.txt -u https://target/FUZZ`). Mask duplicates with `sort -u` or `awk '!seen[$0]++'` before handing it to a heavy fuzzer.
4. When you edit a list, maintain the directory README or add a brief note explaining the source and date so future users understand the provenance.

## Notes

- Because some lists are enormous, they may be stored as compressed files (`.zip`, `.tgz`) or in dedicated subdirectories like `withcount`. Extract only what you need before running, and delete temporary files if you are working in a sensitive environment.
- Data in this repo is for security research and learning—don’t use it against targets you do not own or have permission to test.
- The counts and quality vary between files; always inspect a sample before trusting a list in automation.

## Contribution guidelines

1. Place new wordlists in the folder that matches their use case.
2. Update (or create) a README inside that folder to summarize the source, format and any gotchas.
3. Run `git status` to confirm your changes, then submit a pull request with a short description of what the list adds.

## License

See the top-level directories for any included license files. When no license is provided, assume “no rights reserved” and verify with the upstream author before redistributing. If you need a formal license, reach out to the maintainer before mounting the repository into a project.
