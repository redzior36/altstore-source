# redzior36 Apps — AltStore Source

Adres do dodania w AltStore Classic → Sources → +:

**https://redzior36.github.io/altstore-source/source.json**

Dostępne aplikacje:

- **NextCue 0.6.2 (kompilacja 9)**, wymagany iOS/iPadOS 17.0+. [Wydanie i plik IPA](https://github.com/redzior36/altstore-source/releases/tag/nextcue-v0.6.2). Przypinanie notatek, przesuwanie kart Cues, wyszukiwanie PDF, ręczne numery i eksport z kolorami oraz położeniami kart. Katalogi dodaje się wyłącznie z Plików. IPA do podpisania przez AltStore / SideStore.
- **Apka do Faktur 0.9.2 (kompilacja 4)**, wymagany iOS/iPadOS 26.0+. [Wydanie i plik IPA](https://github.com/redzior36/altstore-source/releases/tag/apka-do-faktur-v0.9.2). Źródło można dodać również w SideStore.

## Publikacja

GitHub Pages publikuje katalog główny gałęzi `main`. Plik `.nojekyll` wyłącza przetwarzanie Jekyll. Ustawienie repozytorium: Settings → Pages → Deploy from a branch → main → /(root). Każdy zapis na `main` aktualizuje źródło.

Alternatywny adres: https://raw.githubusercontent.com/redzior36/altstore-source/main/source.json

## Dodawanie aplikacji

1. Przygotuj IPA przeznaczone do instalacji na urządzeniu. Udostępnij je jako załącznik publicznego GitHub Release, np. w tym repozytorium. Sprawdź pobieranie bez logowania; prywatne wydania i wygasające artefakty Actions nie nadają się do tego źródła.
2. Rozpakuj IPA. Z `Payload/*.app/Info.plist` odczytaj `CFBundleIdentifier`, `CFBundleShortVersionString`, `CFBundleVersion` i `MinimumOSVersion`. Zmierz rozmiar całego IPA w bajtach.
3. Dodaj obiekt do `apps`: `name`, `bundleIdentifier`, `developerName`, `localizedDescription`, publiczne `iconURL`, `versions` i `appPermissions`.
4. W `versions` dodaj `version`, `buildVersion`, datę publikacji `date` w ISO 8601, bezpośrednie `downloadURL`, `size` i ewentualnie `minOSVersion`. Najnowszą wersję umieść pierwszą.
5. Uzupełnij `appPermissions.entitlements` i `appPermissions.privacy` na podstawie rzeczywistej aplikacji oraz rozszerzeń. Nie zakładaj, że uprawnienia są puste.
6. Sprawdź JSON (`python3 -m json.tool source.json`), dostępność wszystkich adresów i zgodność metadanych z IPA. Zapisz zmianę, poczekaj na Pages i odśwież źródło w AltStore.

Format sprawdzony 2026-10-30 według [oficjalnej specyfikacji AltStore](https://faq.altstore.io/developers/make-a-source). To źródło dla **AltStore Classic**; dystrybucja PAL wymaga odrębnego procesu notaryzacji i pakietów ADP.
