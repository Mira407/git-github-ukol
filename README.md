# git-github-ukol
The last of Git
# Git & GitHub – tahák pro VS Code


| Pojem | Co to znamená lidsky |
| --- | --- |
| **Repozitář (repo)** | Složka s projektem, která si pamatuje celou svou historii. |
| **Commit** | Uložená „fotka“ změn se zprávou, co jsi udělal/a. |
| **Branch (větev)** | Paralelní verze projektu. Pracuješ v ní, aniž bys rozbil/a `main`. |
| **Merge** | Spojení jedné větve do druhé. |
| **Push** | Pošle tvoje commity z počítače na GitHub. |
| **Pull** | Stáhne nové commity z GitHubu k tobě (a rovnou je spojí). |
| **Fetch** | Jen se podívá, co je na GitHubu nového – nic nemění. |
| **Clone** | Stáhne si celé repo z GitHubu do počítače. |
| **Fork** | Tvoje vlastní kopie cizího repa na GitHubu. |
| **Pull request (PR)** | Žádost „prosím, přidej moje změny do vaší větve“. |
| **Issue** | Úkol nebo hlášení chyby na GitHubu. |
| **Kolaborátor** | Člověk, který smí zapisovat do tvého repa. |

---

## Pořád dokola

1. **Pull** – stáhni si aktuální verzi (`…` v Source Control → *Pull*).
2. **Vytvoř větev** – klikni na název větve vlevo dole → *Create new branch…*
3. **Uprav soubory** a ulož (`Ctrl+S`).
4. **Stage** – u souboru klikni na `+` (nebo `+` u *Changes* pro všechny).
5. **Commit** – napiš zprávu nahoru do políčka a klikni na *Commit*.
6. **Push** – *Publish Branch* (poprvé) nebo *Sync Changes* (příště).
7. **Pull request** – na GitHubu klikni na *Compare & pull request*.

> [!IMPORTANT]
> Zpráva commitu má říct **co** změna dělá: dobře `Přidat tip na film Duna`, špatně je `asdf`, `fix`, `změny`.

---

## Založení a propojení repa

| Chci… | Jak na to |
| --- | --- |
| **Vytvořit repo** | GitHub → `+` vpravo nahoře → *New repository* → zaškrtni *Add a README* → *Create*. |
| **Stáhnout repo do VS Code (clone)** | Na GitHubu zelené tlačítko *Code* → zkopíruj URL. Ve VS Code `Ctrl+Shift+P` → *Git: Clone* → vlož URL → vyber složku. |
| **Přidat kolaborátora** | Repo na GitHubu → *Settings* → *Collaborators* → *Add people*. Druhý musí pozvánku **přijmout**. |
| **Forknout cizí repo** | Na stránce repa tlačítko *Fork* vpravo nahoře → *Create fork*. Pak svůj fork klonuj jako obvykle. |
| **Upravit README** | Je to obyčejný soubor `README.md` – uprav, commitni, pushni. |
| **Smazat repo** | *Settings* → úplně dole *Danger Zone* → *Delete this repository*. Pozor, nevratné! |

---

## Větve

| Chci… | Jak na to ve VS Code |
| --- | --- |
| **Vytvořit větev** | Klikni na název větve vlevo dole → *Create new branch…* → napiš název. |
| **Přepnout větev** | Klikni na název větve vlevo dole → vyber jinou. |
| **Zmergovat větev do aktuální** | Source Control → `…` → *Branch* → *Merge…* → vyber, **kterou** větev chceš přidat. |
| **Smazat větev lokálně** | `Ctrl+Shift+P` → *Git: Delete Branch…* (nesmíš na ní zrovna být). |
| **Smazat větev na GitHubu** | Po zmergování PR tlačítko *Delete branch*, nebo záložka *Branches* → ikonka koše. |

> [!NOTE]
> Merge se dělá **do větve, na které právě jsi**. Chceš-li dostat `main` do své větve: přepni se na svou větev → *Merge…* → vyber `main`.

---

## Merge conflict – bez paniky

Konflikt = dva lidé změnili **stejný řádek** a Git neví, čí verze je správná. Nic se nerozbilo, jen se musíš rozhodnout ty.

1. VS Code ti soubor s konfliktem ukáže v *Merge Changes* s červeným `!`.
2. Otevři ho. Uvidíš barevné bloky a nad nimi odkazy:
   - **Accept Current Change** – nechat tvoji verzi,
   - **Accept Incoming Change** – vzít tu druhou,
   - **Accept Both Changes** – nechat obě.
3. Případně text ručně uprav, jak má finálně vypadat. Nesmí v něm zůstat značky `<<<<<<<`, `=======`, `>>>>>>>`.
4. Ulož → `+` (stage) → **Commit** → **Push**. Hotovo.

---

## Pull requesty a issues

**Pull request:**

1. Pushni svou větev.
2. Na GitHubu klikni *Compare & pull request* (nebo *Pull requests* → *New*).
3. Napiš název a popis, co PR přidává → *Create pull request*.
4. Druhý člověk ho projde, okomentuje (*Files changed* → klikni na řádek) a klikne **Merge pull request**.
5. Chceš PR ještě upravit? Stačí commitnout a pushnout do **stejné větve** – PR se aktualizuje sám.

**PR z forku:** stejný postup, jen GitHub nabídne poslat PR do **původního** repa (*base repository*). Zkontroluj, že tam je to správné.

**Issue:** záložka *Issues* → *New issue*. Když do popisu PR napíšeš `Closes #3`, issue č. 3 se po zmergování samo zavře.

---

## Stash – „odlož si to na chvíli“

Máš rozdělanou práci a potřebuješ přepnout větev? Source Control → `…` → *Stash* → *Stash*. Změny zmizí a máš čistý stůl. Až se vrátíš: `…` → *Stash* → *Pop Latest Stash*.

---

## Jak vrátit chybu

| Situace | Co udělat |
| --- | --- |
| Upravil/a jsem soubor, ale ještě **necommitnul/a** | U souboru v Source Control ikonka šipky zpět **Discard Changes**. (Tohle je `git restore`.) |
| Commit je **už na GitHubu** a chci ho vrátit | **Revert** – vytvoří nový commit, který změny obrátí. Historie zůstane celá a nikomu nic nerozbiješ. |
| Zmergovaný PR byl chyba | V PR na GitHubu tlačítko **Revert** → vznikne nový PR, který ho vrátí. |


---

## Užitečné zkratky ve VS Code

| Zkratka | Co dělá |
| --- | --- |
| `Ctrl+Shift+G` | Otevře Source Control |
| `Ctrl+Enter` | Commit (když jsi v políčku na zprávu) |
| `Ctrl+Shift+P` | Paleta příkazů – napiš *Git:* a uvidíš všechno |
| `Ctrl+Shift+V` | Hezký náhled Markdownu (třeba tohohle taháku) |
| `Ctrl+K` pak `V` | Náhled Markdownu vedle textu |

---

## Časté problémy

<details>
<summary><b>Push nejde – „Updates were rejected“</b></summary>

Na GitHubu je něco, co ty ještě nemáš. Udělej nejdřív **Pull**, pak znovu **Push**.
</details>

<details>
<summary><b>Nemůžu přepnout větev</b></summary>

Máš neuložené nebo necommitnuté změny. Buď je commitni, nebo je odlož přes **Stash**.
</details>

<details>
<summary><b>Kolaborátor nemůže pushnout</b></summary>

Nejspíš ještě nepřijal pozvánku. Najde ji v e-mailu nebo na GitHubu v notifikacích.
</details>

<details>
<summary><b>Commitnul/a jsem omylem přímo do main</b></summary>

Nevadí, nic nemaž. Řekni to týmu a příště si před prací vytvoř větev. Pokud je změna špatně, použij **Revert**.
</details>