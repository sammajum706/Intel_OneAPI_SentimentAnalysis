# Intel OneAPI SentimentAnalysis

## Our Motivation

Recent research suggests an emerging trend in the use of artificial intelligence to exceed human capabilities. One such application of AI is *Sentiment Analysis*, which shows potential in assessing the performance of products, marketing campaigns, and customer services. The analysis of consumer sentiment enables brands to comprehend their customers and improve their sales by developing strategies based on consumer reactions to various forms of content. Understanding consumer sentiment helps brands to tailor their messaging and advertising to appeal to their target audience, creating a personalized experience for each consumer and deepening their understanding of their customers. However, there is still ample room for improvement in Sentiment Analysis, especially in terms of enhancing its ***efficiency*** and ***effectiveness***.
This repository is about the sentiment analysis problem using SVM based ANN and feature extraction using Word2Vec model where Intel OneAPI toolkits is being integrated for efficient inference and performance

After experimenting with several optimizers for our model, we have determined that the SGD optimizer is the most suitable. This is due to its ability to converge to the minimum of the cost function, introduce random noise for regularization, and handle large datasets with efficiency. The results demonstrate that our model achieves the best performance when using the SGD optimizer, as illustrated in the figure.

<br/><br/>
![Flowchart](https://user-images.githubusercontent.com/75220234/236588785-8d2b840f-8748-4478-a9a4-11a7c419f8e6.jpeg)


## Role of Intel OneAPI toolkits
By utilizing Intel's OneDNN and OneMKL, we developed an application that utilizes the background operation optimization of OneDNN by fusing and reordering operations and reducing memory usage. 
We employed the Intel extension for PyTorch, which provided several benefits, like
increased performance, 
improved efficiency, 
access to Intel-specific features, 
seamless integration,
flexibility.
We observed a significant improvement in runtime and overall speed when using IPEX, as compared to the performance without using IPEX.

We also used Intel Extesion for Scikit Learn and Modin: The drop-in replacement for Pandas which provided several benefits, like
Reduced Memory Usage
Improved Performance 
Scalability
Access to Intel®-specific features like Math Kernel Library

Overall, the library optimizes data ingestion along with algorithmic computation to increase throughput and scalability
<br/><br/>

<img src="/Final_Flow.jpeg" style="margin: 10px;">

<img src="/Optim-Sel.jpeg" style="margin: 10px;">



<br/><br/>

## Our Approach

Firstly, Feature extraction is done using Word2Vec.
We get a final clean dataset that contains its sentiment score and the corresponding feature vector.
After that, we train 2 artificial neural networks(ANN) using the feature vectors of the words extracted with OneDNN being used in the background.
Then, we perform a linear Regression Ensemble of Trained Artificial Neural Networks using Support Vector Machine (SVM).
