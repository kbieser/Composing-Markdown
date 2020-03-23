# Composing documents with Markdown

## Heading level 2 follows

### Level 3

#### 4 Etc

A paragraph of normal text just has to be separate from any sort of text that has flavor (styling).

##### subheading 5 Lists

Lists are pretty easy

- Item 1
- Item 2
  - sub-item on Lists

Let's show off numbered Lists
1. kjklj
2. jkjlkj
3. jljlkj
3. this isn't 3, markdown corrects the list to what it knows is correct

### Bold and italics

Anywhere in a paragraph of text you can make a word or words **bold**, _italic_ or _**both**_. My advice is to just use the asterisks for the bold and the underscores for the italics even though either for either is legal. (2 symbols bold. 1 symbol for italics.). There is no real markdown way to underline that I know of.

### Markdown was created for blogging

(So it is pretty good at links). Let's take a look. Let's google for daring fireball Markdown

All the ways to render links in Markdown can be found here: [Link to github cheatsheet on Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links)

### Code rendering and syntax highlighting

Code in markdown can be rendered two ways, largely depending on length and your preferences. Let's say that you wanted to talk about the `ls` command. To reference it in-line is backtick ls backtick. The backtick key is with the ~. This might be more legible `ls-lh`. So, with single backticks, the code appears in a paragraph, if possible, but looks like a typewriter wrote it.

Code blocks are pretty cool looking. They use triple backticks, and can be used for one or more lines of code in a chunk.

```
# Three backticks start it
# code is in the middle
# three backticks below it end it.
# The normal rules get suspended in code blocks.
```

```bash
for justlane1r1 in `ls *.gz | grep -E '_S[0-9]+_L001_R1_001.fastq.gz'`; do
  echo operating on $justlane1r1 and friends
  stem=${justlane1r1/_L001_R1_001.fastq.gz}
  echo $stem

  for allmatches in "${stem}"*.fastq.gz; do
    unpigz -k $allmatches & #if you have less than 24 cpus just delete the "&"
  done
  wait

  cat "${stem}"_L00?_R1_001.fastq > ${outdir}/"${stem}"_R1.fastq &
  cat "${stem}"_L00?_R2_001.fastq > ${outdir}/"${stem}"_R2.fastq
  wait

  rm "${stem}"_L00?_R?_001.fastq
  pigz ${outdir}/"${stem}"_R?.fastq #you can throttle this a little with "-p 8" for example

done
```

### Images

Images work a lot like links. Let's start by leaching and image from somewhere.
First let's give ourselves [A normal link to the image borrowed from genetics.org](https://www.genetics.org/content/genetics/208/2/473/F1.large.jpg?width=800&height=600&carousel=1) To make the borrowed image show up on our page directly, let's refer back to the cheatsheet and learn that you can do it just like an inline link but put an exclamation point in front of it.

![A normal link to the image borrowed from genetics.org](https://www.genetics.org/content/genetics/208/2/473/F1.large.jpg?width=800&height=600&carousel=1)
