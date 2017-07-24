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