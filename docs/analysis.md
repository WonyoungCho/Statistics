# Python: import module
```
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
from sklearn.linear_model import LogisticRegression
from sklearn.svm import SVC
from sklearn.model_selection import train_test_split
from sklearn.model_selection import cross_validate
from sklearn.datasets import make_classification
```

# Logistic regression
```
def l_regression(df):
    #print(df.head())
    #sns.countplot(x='group', data=df)
    #plt.show()

    Y=df['group']
    X=df.iloc[:,2:(df.shape[1]+1)]

    X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=0.3)

    log_clf = LogisticRegression(solver='lbfgs')
    log_clf.fit(X_train,Y_train)
    score=log_clf.score(X_test, Y_test)
    CR='\033[41m'; CE='\033[0m'
    #print('The data can be divided with'+CR,round(score*100,2),CE+'% accuracy.')

    return score

def plot_accuracy(bfile1,bfile2):
    df = pd.read_csv('./data1/'+bfile1+'.csv')
    scoreList=[]
    for n in range(30):
        score=l_regression(df)
        scoreList.append(score)
    plt.plot(scoreList,label=bfile1+' : '+str(round(np.mean(score),2)))

    df = pd.read_csv('./data1/'+bfile2+'.csv')
    scoreList=[]
    for n in range(30):
        score=l_regression(df)
        scoreList.append(score)
    plt.plot(scoreList,label=bfile2+' : '+str(round(np.mean(score),2)))

    plt.legend()
    plt.ylim(0,1)
    plt.show()
```

# Hierarchy heatmap
```
def plot_heatmap(bfile1,bfile2):
    df=pd.read_csv('./data1/'+bfile1+'.csv').set_index('id').drop(columns='group')

    #sns.heatmap(df, annot=True, linewidths=1, linecolor='black')

    sns.clustermap(df,cmap='RdBu_r')
    plt.show()
```

# Correlation
```
def correlation(df):
    corr = df.iloc[:,1:].corr(method = 'pearson')
    mask = np.zeros_like(corr, dtype=np.bool)
    mask[np.triu_indices_from(mask)] = True
    cmap = sns.diverging_palette(220, 10, as_cmap=True)

    #sns.distplot(df['price'])
    #sns.pairplot(df)
    sns.heatmap(corr, mask=mask, cmap=cmap, annot=True, linewidths=1, linecolor='black')#, fmt='d') # format=integer
    #plt.title('Correlation', fontsize=20)
    plt.show()
```

# Scatter plot
```
def model_regression(df,lst,cnt,color,lgd):
    fig, ax = plt.subplots(3,3)
    model = LinearRegression(fit_intercept=False)

    for j in enumerate(lst):
        a1=[df[j[1]].iloc[cnt-1]]
        for i in range(cnt-2,-1,-1):
            a1min=min(a1)
            a1max=max(a1)
            m=max(abs(a1max),abs(a1min))
            a1.append(a1[-1]+df[j[1]].iloc[i])
        ax.flat[j[0]].scatter(df['price'],a1,c=color[j[1]-1],label=lgd[j[1]-1],marker='.',edgecolors='k',alpha=0.6,linewidths=0.8)
        ax.flat[j[0]].legend()
        #r_sq = model.score(df['price'],a1)
        #ax.flat[r_sq].set_title()

    plt.show()
```
