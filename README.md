# Kaishi 1.5k

Bem-vindo ao repositório público para **Kaishi 1.5k**, um baralho Anki moderno feito para introduzir iniciantes ao vocabulário básico de japonês. Kaishi 1.5k é altamente modular e esta página está aqui para explicar várias opções que você pode usar para personalizar o baralho conforme sua preferência. Aqui está como a frente do baralho é apresentada:

<img src="https://github.com/donkuri/Kaishi/blob/main/pics/front-card.png" alt="Front of a Card in Kaishi 1.5k" style="width: 100%; height: auto">

Como você pode notar, tanto a palavra quanto as frases estão presentes, mas a palavra é destacada na frase, tornando fácil isolar imediatamente a informação importante. Uma vez que você esteja familiarizado com a palavra, a revisão se torna mais rápida, já que a palavra aparece primeiro. Aqui está o verso do baralho padrão:

<img src="https://github.com/donkuri/Kaishi/blob/main/pics/back-card.png" alt="Back of a Card in Kaishi 1.5k" style="width: 100%; height: auto">

Diferentemente da maioria dos baralhos, aqui o furigana mostra a leitura da palavra, com o significado logo abaixo. Além disso, há áudio para a palavra e para a frase disponíveis. Se preferir, também pode adicionar o pitch accent, conforme explicado abaixo. Quaisquer notas relacionadas a esse cartão específico serão exibidas logo abaixo.

## Onde eu consigo o baralho?

Você pode obter o baralho na página de [releases](https://github.com/donkuri/Kaishi/releases/) deste GitHub ou no [AnkiWeb](https://ankiweb.net/shared/info/1196762551), desde que o baralho não esteja passando por revisão. **O baralho é compatível com o Anki 2.1.50 ou superior.**

## Quais opções estão disponíveis para o deck?

Existem várias opções que você pode usar para modificar seus cartões. Para modificá-los, selecione o baralho Kaishi, clique em `Navegar`, escolha qualquer cartão do baralho e clique em `Cartões...` no canto superior direito.

### Pitch Accent

A opção mais importante é se você gostaria de incluir o pitch accent em seus cartões. Atualmente, a questão de se deve ou não aprender pitch accent tende a gerar debates acalorados na comunidade. Optamos por adotar uma abordagem intermediária: os dados de pitch accent estão disponíveis para você, e você decide se deseja usá-los. Se decidir não usar, sempre poderá ativá-los posteriormente. Habilitar o pitch accent é fácil. Aqui estão as opções de cartão sob o `Modelo de trás` para o baralho (clique no ponto pequeno acima da barra de `Pesquisa`).

```CSS
<div lang="ja">
{{furigana:Word Furigana}}

<!-- Essa parte habilita o pitch accent.

{{#Pitch Accent}}
	<br><div style='font-size: 24px'>{{Pitch Accent}}</div>
{{/Pitch Accent}} 

-->

<div style='font-size: 25px; padding-bottom:20px'>{{Word Meaning}}</div>
<div style='font-size: 25px;'>{{furigana:Sentence Furigana}}</div>
<div style='font-size: 25px; padding-bottom:10px'>{{Sentence Meaning}}</div>

{{Word Audio}}
{{Sentence Audio}}

{{#Notes}}
	<br>
	<div style="font-size: 20px; padding-top:12px">Note: {{Notes}}</div>
{{/Notes}}

<!-- Esta parte habilita notas sobre o pitch accent.

{{#Pitch Accent Notes}}
<div style="font-size: 20px; width: fit-content; max-width:40vw; margin: auto">
	<details><summary>Pitch Accent Notes</summary>
		<br>{{Pitch Accent Notes}}
	</details>
</div>
{{/Pitch Accent Notes}}

-->
</div>
```

Para habilitar o pitch accent, você só precisa remover todos os `<!--` e os `-->` que são partes que representam comentários, assim: 

```CSS
<div lang="ja">
{{furigana:Word Furigana}}

{{#Pitch Accent}}
	<br><div style='font-size: 24px'>{{Pitch Accent}}</div>
{{/Pitch Accent}} 

<div style='font-size: 25px; padding-bottom:20px'>{{Word Meaning}}</div>
<div style='font-size: 25px;'>{{furigana:Sentence Furigana}}</div>
<div style='font-size: 25px; padding-bottom:10px'>{{Sentence Meaning}}</div>

{{Word Audio}}
{{Sentence Audio}}

{{#Notes}}
	<br>
	<div style="font-size: 20px; padding-top:12px">Note: {{Notes}}</div>
{{/Notes}}

{{#Pitch Accent Notes}}
<div style="font-size: 20px; width: fit-content; max-width:40vw; margin: auto">
	<details><summary>Pitch Accent Notes</summary>
		<br>{{Pitch Accent Notes}}
	</details>
</div>
{{/Pitch Accent Notes}}
</div>
```

### Opções secundárias

Existem algumas opções secundárias que você pode modificar.

#### Furigana
Se você desja remover o furigana, simplesmente remova as partes que falam `furigana:` do modelo de trás.

#### Outras opções de cartão

Você poderia mudar completamente o tipo de cartões que deseja ver. Aqui está o `Modelo da Frente` do Kaishi 1.5k:

```CSS
<div lang="ja">
{{Word}}
<div style='font-size: 20px;'>{{Sentence}}</div>
</div>
```

As you can see, we only have the word and the sentence. If you would like *sentence* cards, simply take out the `{{Word}}` part, or put `Sentence` inside instead and take out the rest. If you would like *word* cards, simply take out the `<div style='font-size: 20px;'>{{Sentence}}</div>` part. If instead you would like *audio* cards, take out everything and add `{{Word Audio}}`, `{{Sentence Audio}}` or both if you would like both.

#### Changing the fonts, font size or other styling options

Here is the `Styling` template of Kaishi 1.5k:

```CSS
.card {
 font-family: "ヒラギノ角ゴ Pro W3", "Hiragino Kaku Gothic Pro", "Noto Sans JP", Osaka, "メイリオ", Meiryo, "ＭＳ Ｐゴシック", "MS PGothic", "MS UI Gothic", sans-serif;
 font-size: 44px;
 text-align: center;
}

/* This part defines the bold coolor. */
b{color: #5586cd}
```

You can find the various styling options [here](https://docs.ankiweb.net/templates/styling.html). As you can see, Kaishi 1.5k uses very little options in the style tab directly. You can change the `font-family` option to get different fonts, `font-size` to change the font size and `text-align` to change the alignment of the text, for instance if you'd like the text to be left aligned. By default, Kaishi 1.5k colors **bold** words. The option to change this is `b{color: }` as you can see above. Simply put a hexcode or a color name like `red` to get that color instead. If you would like no color, simply take out the whole `b{color: }` part.

## How to import Kaishi 1.5k on top of another deck

If you already started Core2k or Tango N4-N5 (or some other similar deck) and you would like to switch to Kaishi 1.5k, you can follow these steps written by [Kuuube](https://github.com/Kuuuube).

1. Import Kaishi normally with the .apkg file.
2. Go to `File > Export...` and export the Kaishi deck using `Notes in Plain Text (.txt)`. Leave all other settings default.
3. Delete the Kaishi deck.
4. Select the deck you want to import Kaishi on top of, select `Browse`, click any card, press `ctrl + a`, and select `Notes > Change Note Type...` on the top left menu.
5. Change to the `Kaishi 1.5k` note type. Make sure the `Word` field in the `New` column shows the field your deck uses for the word next to it.
    If you don't intend to delete any cards from your current deck that are not in Kaishi, make sure your other fields are lined up to the correct places too. Otherwise you can use the defaults and click `Save`.
6. Import the Kaishi .txt file exported in step 2.
7. When importing, make sure the Notetype is set to `Kaishi 1.5k` and the Deck is set to the deck you want to import on top of. 
  If you intend on deleting cards not in Kaishi, add the tag `Kaishi` in the `Tag all notes` option.
8. Click `Import`.
9. To delete cards not in Kaishi, select your deck, click `Browse`, select your deck in left menu, append ` -tag:Kaishi` to the search bar, select any card, press `ctrl + a`, on the top left menu and go to `Notes > Delete`.

**If you're importing on top of Core 2.3k, please see [this](https://github.com/Manhhao/anki.transfer-review-history).**

## The genesis of the deck

This deck has its origin in a discussion between Tyogin and myself in the [TMW discord server](https://learnjapanese.moe/join/). We were both lamenting the fact that the popular beginner decks at the time had annoying flaws. Beginners kept getting confused when using Core 2k and Tango due to various issues. Tango had some obscure words in it such as ナンプラー which is a Thai fish sauce and many people weren't really interested in all the basic phrases and country names taking up such a large amount of the deck. The deck's fields were formatted terribly which made it impossible to use the deck in a different way than was originally intended, which was sentence cards. Core 2k on the other hand was modular, but had multiple mistranslations, missing or unrelated pictures and some of the sentences weren't very useful, sometimes not even reflecting the meaning of the word used.

Both of these issues were annoying enough that we would get beginners asking questions about it every two weeks. Tyogin proposed we fix the issue ourselves and a small team was assembled to fix these issues. We mostly took data from Core2k, Core10k, Tango N4 and Tango N5. We then combined the data, sorted the words by frequency using various Yomichan/Yomitan frequency dictionaries and selected around 1500 words. We then fixed the translations for each word, chose the best sentence for each word and fixed the sentence if it needed fixing. We had to fix roughly 120 sentences out of the 1500 we chose. After this, we generated audio for words that were missing proper audio, and a team of two people (Karifurai and cindsa) verified the pitch accent data we got from [AJT Japanese](https://ankiweb.net/shared/info/1344485230) as well as adding pitch accent notes for words that needed it. We then took out silence on the cards and normalized the audio level between the various files. On top of that, we also generated furigana from AJT Japanese for the words and the sentences. After this, we designed a basic hint targeted sentences card CSS to be used on the default version of the deck. Finally, multiple people proofread the deck to make sure we had as few errors as possible.

Kaishi, written 開始 means "start, beginning". We thought this fit properly so we decided on this name. Hopefully, this deck will be a wonderful start to your Japanese learning journey.

## Translation of the deck

If you are interested in translating the deck in your native language, please make an issue on [the GitHub tracker](https://github.com/donkuri/Kaishi/issues).

## Credits

This deck was made with the help of these people:

[栗](https://github.com/donkuri/) - main architect, all technical aspects, translations, proofreading

Tyogin - main architect, reordered the first 200 cards, changed the sentences, proofreading

shoui - proofreading the entire deck, fixed translations

Julian - helped add notes and checked some sentence translations

karifurai - verified the pitch accent for the first 750 cards and added pitch notes

cindsa - verified the pitch accent for the last 750 cards and added pitch notes

[Kuuube](https://github.com/Kuuuube) - suggested the use of FFmpeg, wrote the transferring cards to Kaishi 1.5k section above

[stephenmk](https://github.com/stephenmk) - ran the Jmdict Furigana tool on Kaishi 1.5k to fix furigana, see v1.3.0

These tools were used in the creation of the deck:

[AJT Japanese](https://github.com/Ajatt-Tools/Japanese) - pitch accent, furigana and some of the audio were generated using this add-on

[FFmpeg](https://ffmpeg.org/) - used to take out some silent parts in various audio files

[Tenacity](https://tenacityaudio.org/) - used to edit clipping sounds in various audio files

We also got various ideas from multiple members of the TMW discord server, including the name of the deck itself.




