# LLM atmiņas plānotājs (latviski)

Bezmaksas bezsaistes kalkulators LLM modeļa darbināšanas atmiņai: modeļa svari, kvantizācijas formāta papildapjoms, KV kešs un izpildes rezerve, aprēķināti atsevišķi.

**Tiešsaistē:** https://mineshop007.github.io/llm-atminas-planotajs/

## Formulas

- **Neapstrādāti svari (GiB)** = parametri × 10⁹ × biti ÷ 8 ÷ 2³⁰
- **Formāta papildapjoms** = svari × papildapjoms (%) — regulējams pieņēmums (pēc noklusējuma 15 %)
- **KV kešs (GiB)** = 2 × slāņi × KV galvas × galvas dimensija × tokeni × paralēlās secības × baiti uz vērtību ÷ 2³⁰
- **Kopā** = svari + papildapjoms + KV kešs + rezerve

Piemērs (tests): 8B 4 bitos, 32 slāņi, 8 KV galvas, dimensija 128, konteksts 8 192 tokeni, FP16 kešs → KV kešs = 1,00 GiB.

## Ierobežojumi

Novērtējums blīviem transformeriem ar pilnu uzmanības kešu; tas nav etalontests un negarantē ātrumu. Slīdošā loga, MLA, hibrīdās vai MoE arhitektūras var ievērojami atšķirties. Vairāki GPU neveido vienu atmiņas bloku.

## Testi

```
node test.js
```

## Par projektu

Latviešu versija rīkam [LLM-Speicherplaner](https://github.com/Mineshop007/llm-speicher-planer) (arī [franču valodā](https://github.com/Mineshop007/planificateur-memoire-llm)), ko nodrošina [Mineshop.eu](https://mineshop.eu/lv) — [videokartes](https://mineshop.eu/lv/graphic-card-gpu-en) un [AI darbstacijas](https://mineshop.eu/lv/ai-workstation). Bez sīkfailiem, bez analītikas, ievadītie dati netiek nekur sūtīti.
