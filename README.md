# German Wikipedia Text Corpus
This is a german text corpus from Wikipedia. It is cleaned, preprocessed and sentence splitted. It's purpose is to train NLP embeddings like [fastText](https://fasttext.cc/) or [ELMo Deep contextualized word representations](https://allennlp.org/elmo).

The benefit of this text corpus is that it does not just contain the article space of the wiki. It also contains the comments for a larger text corpus and a more sloppy language. This should improve the quality of downstream tasks when you process conversations like mails, chats, tweets or support tickets.

## How this corpus has been generated
We used a wikipedia dump as the data source.
- They can be downloaded here: https://dumps.wikimedia.org/
- Mirror here: https://dumps.wikimedia.org/mirrors.html
- `dewiki-20181001-pages-meta-current.xml.bz2`was used because this dump also contains the comments

Then the tool [WikiExtractor](https://github.com/attardi/wikiextractor) was used to extract the xml dump. To also include the discussion the WikiExtractor tool has been modified:
```
def keepPage(ns, page):
    if ns != '0' and ns != '1': # Aritcle and Talk
        print('skipped ns:', ns)
        return False
    # remove disambig pages if desired
    if options.filter_disambig_pages:
        for line in page:
            if filter_disambig_page_pattern.match(line):
                return False
    return True
```

[...]

## Download
You can download the texts here: 
- [wiki-all-shuf.tgz.part-00](https://github.com/t-systems-on-site-services-gmbh/german-wikipedia-text-corpus/releases/download/files_2/wiki-all-shuf.tgz.part-00)
  - MD5: 9cd27b9a22ee4de391435b4bcbb30428 
  - SHA1: 66ccc99ccfeb4b546f9c888af9b23e5fc1a67236
- [wiki-all-shuf.tgz.part-01](https://github.com/t-systems-on-site-services-gmbh/german-wikipedia-text-corpus/releases/download/files_2/wiki-all-shuf.tgz.part-01) 
  - MD5: bf187bdda21ea9f7af1ecdf085ca54d5 
  - SHA1: 73749be0285a6e359dead08acf65b33e9a55c9b4
- [wiki-all-shuf.tgz.part-02](https://github.com/t-systems-on-site-services-gmbh/german-wikipedia-text-corpus/releases/download/files_2/wiki-all-shuf.tgz.part-02) 
  - MD5: b887df79f54d7d36d3da22e5e6f8add1 
  - SHA1: f9c773821bee112b976ae5247ac55ffdba6e20f7
- wiki-all-shuf.tgz 
  - MD5: 51ddcca730dca6e48c29d6339c2059f9 
  - SHA1: f1c7ef0245abca47d3be2657ac4c345a3dc8d121

## Unpack
Using these commands you can unpack the files (Linux and macOS):
```
cat wiki-all-shuf.tgz.part-* > wiki-all-shuf.tgz
tar xvfz wiki-all-shuf.tgz
```

## License
As Wikipedia itself this is published under [Creative Commons Attribution-ShareAlike 3.0 Unported license](https://de.wikipedia.org/wiki/Wikipedia:Lizenzbestimmungen_Creative_Commons_Attribution-ShareAlike_3.0_Unported). 
