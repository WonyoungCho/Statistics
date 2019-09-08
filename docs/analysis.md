# Python library
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

# Regression
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

