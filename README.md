# Word2vec/Word Embedding
The algorithm is optimized by the Word2vec that generate word vectors by given the words./特定词的词向量生成。
This method boosts the train speed and gets a better result./算法加速了训练过程，并且得到了更好的结果。

# Word2vec API

1.初始化

int InitWord2vec(const char * data,const char * sLicenseCode);

2.初始化训练参数

int InitPara(int size,const char * train,const char * entity,int model,float alp,const char * outfile,int win,float sam,int h,int neg,int threads, int it,int mincount);

3.训练

int Train();

4.加载模型

int LoadModel(const char * model);

5.计算词向量

const char * CalculateWord(const char * word,int N);

# Demo

```java
public static void main(String[] args){
        int i=CLibraryWord2vec.Instance.InitWord2vec("Data/","");
        System.out.println(i);
        /**
        *corpus.txt,分词后的语料
        *words-all.txt，需要构建关系的词，可以全部指定
        *vectors.txt，生成的结果向量
        **/
        CLibraryWord2vec.Instance.InitPara(200, "corpus.txt", "words-all.txt", 1, Float.parseFloat("0.025"), "vectors.txt", 8, Float.parseFloat("1e-4"), 1, 25, 1, 15, 1);
        CLibraryWord2vec.Instance.Train();
        //加载模型
        CLibraryWord2vec.Instance.LoadModel("vectors.txt");
        //计算
        //参数1：输入词
        //参数2：结果个数
        String result=CLibraryWord2vec.Instance.CalculateWord("中国",10);
        String result1=CLibraryWord2vec.Instance.CalculateWord("秘鲁",10);
        System.out.println(result);
        System.out.println(result1);
}
```
