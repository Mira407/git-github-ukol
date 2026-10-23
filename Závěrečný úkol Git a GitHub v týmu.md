# Závěrečný úkol: Git a GitHub v týmu


## O co jde

Ve dvojici napíšete malý program v Pythonu, který šifruje a dešifruje text **Caesarovou šifrou** (každé písmeno se posune v abecedě o daný počet míst, např. o 3: `a → d`, `ahoj → dkrm`). Program má dvě funkce: jeden z vás napíše **šifrování**, druhý **dešifrování**. Programování je tu jen záminka – hodnotí se hlavně to, **jak pracujete s Gitem a GitHubem**. Stačí, aby program fungoval; nemusí být dokonalý.

- **Týmy:** dvojice. Jeden z vás je **A** (vlastník repozitáře), druhý **B** (kolaborátor). Kdo je kdo, napište do README.
- **Prostředí:** VS Code (panel Source Control) a web GitHubu. Terminál nepotřebujete.
- **Důležité:** všechno, co uděláte, je vidět v historii repozitáře. Nic nemažte ani nepřepisujte – zadavatel kontroluje commity, větve a pull requesty přímo na GitHubu.

Každý krok má u sebe, **kdo** ho dělá (A, B, nebo oba). Pokud jste ve trojici, třetí člen se chová jako B.

## Část 1 – Založení repozitáře

Cíl: mít společný repozitář, do kterého můžete oba zapisovat, a mít ho otevřený ve VS Code.

1. **A:** Na GitHubu vytvořte nový **veřejný** repozitář `sifrovac` a zaškrtněte vytvoření README.
2. **A:** V *Settings → Collaborators* přidejte **B** jako kolaborátora. **B** pozvánku přijme (přijde e-mailem nebo je v notifikacích).
3. **Oba:** Naklonujte repozitář do VS Code (*Clone Repository* a URL repozitáře) a přihlaste se ke GitHubu, pokud vás VS Code vyzve.
4. **A:** Upravte README tak, aby obsahovalo nadpis projektu, jednu větu, co program dělá, a jména členů týmu s rolemi A a B.
5. **A:** Vytvořte soubor `sifra.py` s kostrou programu (zkopírujte ji níže). Funkce zatím nic nedělají, jen vrátí text beze změny.
6. **A:** Obojí commitněte s rozumnou zprávou (např. `Přidat README a kostru programu`) a pushněte.
7. **B:** Udělejte *Pull*, ať máte všechno u sebe.

```python
def zasifruj(text, posun):
    # TODO (A): posuň každé písmeno o 'posun' míst dopředu
    return text


def desifruj(text, posun):
    # TODO (B): posuň každé písmeno o 'posun' míst dozadu
    return text


zprava = "ahoj svete"
tajne = zasifruj(zprava, 3)
print("Zasifrovano:", tajne)
print("Desifrovano:", desifruj(tajne, 3))
```

**Pravidlo pro zprávy commitů:** krátce a konkrétně, co změna dělá. Zprávy typu `asdf`, `fix` nebo `změny` se počítají jako chyba.

## Část 2 – Práce ve větvích a pull requesty

Cíl: nikdo nepíše přímo do `main`. Každá změna jde přes vlastní větev a pull request, který schválí ten druhý.

1. **Oba:** Z aktuálního `main` si ve VS Code vytvořte vlastní větev: A `sifrovani`, B `desifrovani`.
2. **A** ve své větvi napíše funkci `zasifruj`, **B** funkci `desifruj`. Pracujte po malých krocích a **každý krok commitněte zvlášť** – ve větvi musí být aspoň 3 commity, například:
   - posun malých písmen (`a → d`),
   - přetečení na začátek abecedy (`z → c` při posunu 3),
   - mezery a ostatní znaky zůstanou beze změny.
3. **Oba:** Program si spusťte a vyzkoušejte, že vaše funkce dělá, co má.
4. **Oba:** Pushněte větev na GitHub (*Publish Branch*).
5. **Oba:** Na GitHubu otevřete **pull request** ze své větve do `main`. Do popisu napište, co PR přidává.
6. **Oba:** Projděte PR toho druhého a napište do něj **aspoň jeden komentář** (dotaz, návrh nebo pochvalu konkrétního řádku).
7. **Autor PR:** Na komentář zareagujte – buď další změnou (commit + push do stejné větve, PR se sám aktualizuje), nebo odpovědí.
8. **Ten druhý:** PR **zmergujte** (merge dělá vždy ten, kdo PR nepsal).
9. **Oba:** Přepněte se ve VS Code zpět na `main`, udělejte *Pull* a spusťte program. Na výstupu by teď mělo být `dkrm vyhwh` a pak zase `ahoj svete`.

Jelikož oba upravujete stejný soubor, může při druhém merge vzniknout **merge conflict**. Pokud se to stane, vyřešte ho ve VS Code stejně jako na hodině (postup je i v taháku) a do PR napište jednou větou, jak jste ho vyřešili.

## Část 3 – Issue, úklid větví a synchronizace

Cíl: vyzkoušet si, jak se na GitHubu práce **zadá** (issue), **udělá** (větev + PR) a **uzavře** (issue se zavře samo). Na konci po sobě uklidíte větve.

Program zatím šifruje pevně zadanou zprávu `"ahoj svete"`. Úkolem je, aby se uživatele zeptal na text a posun sám.

**Krok 1 – A založí issue (na GitHubu)**

1. V repozitáři otevřete záložku *Issues* → *New issue*.
2. Nadpis: „Program se má uživatele zeptat na text a posun“. Do popisu: „Místo pevně zadané zprávy použít `input()`.“
3. Vpravo u *Assignees* vyberte **B**.
4. Klikněte na *Create*. Issue dostane číslo (nejspíš **#1**) – je vidět v nadpisu a B ho bude potřebovat.

**Krok 2 – B si stáhne aktuální verzi (ve VS Code)**

1. Přepněte se na větev `main` (klik na název větve vlevo dole).
2. *Fetch* (`…` v Source Control → *Fetch*) – zjistí, co je na GitHubu nového.
3. *Pull* – stáhne to k vám. V `main` jsou teď obě funkce z části 2. Bez tohoto kroku byste pracovali se starou verzí.

**Krok 3 – B vyřeší issue ve vlastní větvi**

1. Vytvořte větev `issue-1`.
2. V `sifra.py` přepište konec programu takto (pozor na `int()` – `input()` vrací text, bez převodu na číslo program spadne):

```python
zprava = input("Zadej text: ")
posun = int(input("Zadej posun: "))
tajne = zasifruj(zprava, posun)
print("Zasifrovano:", tajne)
print("Desifrovano:", desifruj(tajne, posun))
```

3. Program spusťte a vyzkoušejte.
4. Commit (např. `Načítat text a posun od uživatele`) → *Publish Branch*.

**Krok 4 – Pull request, který zavře issue**

1. **B:** Na GitHubu otevřete PR z `issue-1` do `main`.
2. **B:** Do **popisu** PR napište `Closes #1` (číslo vašeho issue). Podle toho GitHub pozná, že PR issue řeší. Musí to být v popisu, ne jen v komentáři.
3. **A:** PR zkontrolujte a zmergujte.
4. Issue se v tu chvíli **samo zavře**. V *Issues → Closed* u něj uvidíte odkaz na PR, který ho vyřešil.

**Krok 5 – Úklid větví (oba)**

Větve `sifrovani`, `desifrovani` a `issue-1` už nikdo nepotřebuje. Každá existuje na dvou místech, takže je smažete dvakrát:

- **Na GitHubu:** po zmergování PR tlačítko *Delete branch*. Pokud jste ho přeskočili: záložka *Branches* (přes počet větví nad seznamem souborů) → ikonka koše. Stačí, když to udělá jeden z vás.
- **Ve VS Code (každý u sebe):** přepněte se na `main` (větev, na které právě jste, smazat nejde) → `Ctrl+Shift+P` → *Git: Delete Branch…* → vyberte větev. Opakujte pro každou větev.
- **Volitelně:** `Ctrl+Shift+P` → *Git: Fetch (Prune)* – VS Code zapomene větve, které už byly smazány na GitHubu (např. `origin/sifrovani`).

**Krok 6 – Kontrola (oba)**

*Pull* na `main` a spusťte program. Musí se zeptat na text a posun a vypsat zašifrovanou i dešifrovanou verzi. V *Branches* na GitHubu má zbýt jen `main`.

## Část 4 – Příspěvek do cizího projektu (fork)

Cíl: přispět do repozitáře, kam nemáte právo zapisovat – přesně tak se přispívá do open-source projektů. Tuto část dělá **každý sám**.

Zadavatel připraví třídní repozitář (odkaz dostanete na teamsy), ve kterém je složka `studenti/`.

1. Udělejte **fork** třídního repozitáře do svého účtu.
2. Svůj fork naklonujte do VS Code.
3. Vytvořte větev `pridat-jmeno` a v ní soubor `studenti/prijmeni-jmeno.md` s:
   - odkazem na váš týmový repozitář,
   - krátkým vzkazem zašifrovaným vaším programem a posunem, aby ho ostatní mohli rozluštit,
   - jednou větou, co pro vás bylo na Gitu nejtěžší.
4. Commit + push do svého forku.
5. Na GitHubu otevřete **pull request z vašeho forku do třídního repozitáře**.

Zadavatel PR zkontroluje a zmerguje. Pokud vás požádá o úpravu, udělejte ji ve stejné větvi – PR se aktualizuje sám.

## Odevzdání a pravidla

Odevzdáváte dva odkazy do Teamsu PVI

- odkaz na **týmový repozitář** `sifrovac` (odevzdává A za oba),
- odkaz na **váš pull request** do třídního repozitáře (každý sám).

**Pravidla:**

- Repozitář nechte veřejný a **nemažte ho**, dokud není úkol ohodnocený.
- Do `main` se nepíše napřímo. Commit přímo do `main` (kromě README a kostry programu v části 1) se počítá jako chyba.
- Každý člen týmu musí mít v repozitáři vlastní commity – zadavatel to vidí v *Insights → Contributors*.
- Když se něco pokazí, nemažte repozitář a nezačínejte znovu. Napište do issue, co se stalo, a opravte to dalším commitem – i to je práce s Gitem.
