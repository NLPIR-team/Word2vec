# Word2vec/Word Embedding
The algorithm is optimized by the Word2vec that generate word vectors by given the words./特定词的词向量生成。
This method boosts the training speed and gets a better result./算法加速了训练过程，并且得到了更好的结果。

# Word2vec API

1.初始化
int InitWord2vec(const char * data,const char * sLicenseCode);

2.初始化训练参数
//size：词向量维度
//train:语料
//entity:词典
//model：CBOW：1和SKip-gram：0
//outfile:输出模型
//threads：线程数
int InitPara(int size,const char * train,const char * entity,int model,float alp,const char * outfile,int win,float sam,int h,int neg,int threads, int it,int mincount);

3.训练
//训练
int Train();

4.加载模型
//model模型位置
int LoadModel(const char * model);

5.计算词向量
//word：输入词，N输出词个数
const char * CalculateWord(const char * word,int N);

# Build Train File

1.train file
Using the NLPIR, the corpus contains words that like english that splited by the " " without POS info.
//使用中科院分词，将词以空格分开，存入文件，生成语料。

2.make dict
We optimized the algorithm by add dict which will be projected to the vector space, and the word out of the dict will boost the training speed.
//将需要生成词向量的词整理到词典，以加速训练，也可将所有词作为词典

3.set the out model
The outfile is the model the generated by the method.
//设置输出模型

# Demo

```
		//train
		int i=CLibraryWord2vec.Instance.InitWord2vec("Data/","");
		System.out.println(i);
		CLibraryWord2vec.Instance.InitPara(200, "dang.bin", "words-all.txt", 1, Float.parseFloat("0.025"), "vectors.txt", 8, Float.parseFloat("1e-4"), 1, 25, 1, 15, 1);
		CLibraryWord2vec.Instance.Train();
		//get words
		CLibraryWord2vec.Instance.LoadModel("vectors.txt");
		String result=CLibraryWord2vec.Instance.CalculateWord("红岩精神",10);
		String result1=CLibraryWord2vec.Instance.CalculateWord("中国梦",10);
		System.out.println(result);
		System.out.println(result1);
```