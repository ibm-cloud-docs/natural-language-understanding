---

copyright:
  years: 2015, 2020
lastupdated: "2020-07-27"

subcollection: natural-language-understanding

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:deprecated: .deprecated}
{:preview: .preview}
{:beta: .beta}
{:tip: .tip}
{:note: .note}
{:pre: .pre}
{:important: .important}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Evaluating sentiment model quality
{: #evaluating-sentiment-model-quality}

This tutorial explains how to train a custom sentiment custom model and measure the quality of the model by using provided Python scripts. For more information about the API methods used, see [Creating a custom sentiment model](/docs/natural-language-understanding?topic=natural-language-understanding-customizing#custom-sentiment).
{: shortdesc}

The following training and testing data that is used in the tutorial is from [https://nlp.stanford.edu/sentiment/](https://nlp.stanford.edu/sentiment/){: external}.

- [CNSST_train.csv](https://github.com/watson-developer-cloud/doc-tutorial-downloads/blob/master/natural-language-understanding/CNSST_train.csv){: external}
- [CNSST_test.csv](https://github.com/watson-developer-cloud/doc-tutorial-downloads/blob/master/natural-language-understanding/CNSST_test.csv){: external}

You can also use your own sentiment data to complete the tutorial. For more information about the sentiment training data format, see [Sentiment training data requirements](/docs/natural-language-understanding?topic=natural-language-understanding-customizing#sentiment-training-data-requirements).

## Step 1: Create a custom sentiment model
{: #create-a-custom-sentiment-model}

1. Download the Python script [`sentiment_custom.py`](https://github.com/watson-developer-cloud/doc-tutorial-downloads/blob/master/natural-language-understanding/sentiment_custom.py).
2. Download the example corpus file [`CNSST_train.csv`](https://github.com/watson-developer-cloud/doc-tutorial-downloads/blob/master/natural-language-understanding/CNSST_train.csv) to be used with the `sentiment_custom.py` script. You can use the provided corpus file or choose one of your own. By default, the `CNSST_train.csv` file must exist in the same directory as the `sentiment_custom.py` script.
3. The script uses the Python `requests` library for HTTP requests to the service. Use `pip` or `easy_install` to install the library for use by the script, for example:

    ```sh
    pip install requests
    ```
    {: pre}

    For more information about the library, see [https://pypi.python.org/pypi/requests](https://pypi.python.org/pypi/requests).
4. Edit the script to replace the password string `YOUR_API_KEY` with the API key from your {{site.data.keyword.nlushort}} credentials:

    ```
    password = "YOUR_API_KEY"
    ```
    {: pre}

5. Edit the script to replace the url string `YOUR_URL` with the URL for your service instance as provided in your service credentials:

    ```
    url = "YOUR_URL"
    ```
    {: pre}

6. Run the script by entering the following command:

    ```sh
    python3 sentiment_custom.py
    ```
    {: pre}

The new sentiment custom model takes about 30 minutes to finish training. When the model **status** is `available`, the model is ready to use. Make a note of the `model_id` in the output of the `sentiment_custom.py` script. For more information about how to check the status, see [Checking the status of sentiment models](/docs/natural-language-understanding?topic=natural-language-understanding-customizing#checking-status-of-sentiment-models). Alternatively, you can follow step 2 in the script `sentiment_custom.py` to get the status of the model.

## Step 2: Measure model quality
{: #measure-model-quality}

1. Download the Python script [`sentiment_quality.py`](https://github.com/watson-developer-cloud/doc-tutorial-downloads/blob/master/natural-language-understanding/sentiment_quality.py){: external}.
2. If you trained with the `CNSST_train.csv` corpus, download the example test corpus [`CNSST_test.csv`](https://github.com/watson-developer-cloud/doc-tutorial-downloads/blob/master/natural-language-understanding/CNSST_test.csv){: external} to use with the `sentiment_model.py` script. If you didn't use the `CNSST_test.csv` training corpus, use a test corpus that resembles the training data that you used. Save the corpus to the same directory as the `sentiment_quality.py` script.
3. If your corpus file has a different file name, replace `CNSST_test.csv` in the script with the name of your file.
4. Run the script with the `-h` option to read about the options:

    ```sh
    python3 sentiment_quality.py -h
    ```
    {: pre}

5. Run the following example command to evaluate your model. Replace the values in the example with the information from your service instance (`{apikey}` and `{url}`), your custom model, and testing data.

    ```sh
    python3 sentiment_quality.py -p {api_key} -l en -url {url}/v1/analyze?version=2019-07-12 -m e2abbc8a-7714-4g67-8c13-67e64c8fb4de -d CNSST_test.csv
    ```
    {: pre}

    where:
    - `-p` is the  {{site.data.keyword.nlushort}} API key
    - `-l` is the language code
    - `-url` is the {{site.data.keyword.nlushort}} service instance URL
    - `-m` is the custom model ID
    - `-d` is the testing data file
