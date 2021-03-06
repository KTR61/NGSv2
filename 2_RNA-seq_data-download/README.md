# RNA-seqデータの取得・変換  
- fastqファイルを保存するディレクトリを作成  
  - ```mkdir ~/Documents/expression/seq```  
  - ```cd ~/Documents/expression/seq```  
- Runinfo Table と Accession List を上記ディレクトリにダウンロード  
- fasterq-dumpを用いてRNA-seqデータをダウンロード（2020/02/12 タイポがありました。[Twitterにてご報告くださった方](https://twitter.com/takatoh1/status/1212744854045786120)ありがとうございました。）  
  - ~~```cat SRR_Acc_List.txt | while read line; do cmd="fasterq-dupm --split-files ${line}; gzip ${line}*fastq"; eval ${cmd}; done```~~  
  - ```cat SRR_Acc_List.txt | while read line; do cmd="fasterq-dump --split-files ${line}; gzip ${line}*fastq"; eval ${cmd}; done```  
- ダウンロードしたファイルを一覧  
 - ```ls -lh *fastq.gz```  
 - ```ls -lh *fastq.gz | wc -l```  
- 上記で一部のファイルがダウンロードから漏れることがあるようです（[Twitter](https://twitter.com/takatoh1/status/1212744854045786120)）。その場合は抜けているファイルのID（例：SRR0000000）を個別に指定した上でfasterq-dumpを実行してください。  
 - ```fasterq-dump --split-files SRR0000000```
