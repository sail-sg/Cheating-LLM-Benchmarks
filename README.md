<h1 align='center' style="text-align:center; font-weight:bold; font-size:2.0em;letter-spacing:2.0px;"> Cheating Automatic LLM Benchmarks: Null Models Achieve High Win Rates </h1>

<p align='left' style="text-align:left;font-size:1.2em;">
<b>
    [<a href="h" target="_blank" style="text-decoration: none;">arXiv</a>] 
</b>
</p>

# Craft the null response

Run [notebook_gpt4/gpt-4-1106-preview_vs_nil.ipynb](notebook_gpt4/gpt-4-1106-preview_vs_nil.ipynb) to get the null response augmented with the adversarial string. 


# Evaluation

## Step 1: Prepare the submission

Run [01_prepare_submission.ipynb](./01_prepare_submission.ipynb) to craft the null model submission.

## Step 2: Evaluate the submission using alpaca-eval

To install the stable release of AlpacaEval 2.0, run

```bash
pip install alpaca-eval
```

Then you can use it to evaluate the submission as follows:

```bash
export OPENAI_API_KEY=<your_api_key> # for more complex configs, e.g. using Azure or switching clients see client_configs/README.md 
alpaca_eval --model_outputs 'example/outputs.json' 
```

## Step 3 (Optional): Re-evaluate the submission for further analysis

Run [02_re_evaluate_submission.ipynb](./02_re_evaluate_submission.ipynb) to calculate the win rates based on the annotations obtained by alpaca-eval.

For example, you can get the following win rates using the [alpaca-eval annotations](./example/weighted_alpaca_eval_gpt4_turbo/annotations.json) of our null model.

```
{'win_rate': 76.91979180386511, 
'standard_error': 0.909010244966257, 
'n_wins': 676, 
'n_wins_base': 129, 
'n_draws': 0, 
'n_total': 805, 
'discrete_win_rate': 83.97515527950311,
'length_controlled_winrate': 86.45780691307944, 
'lc_standard_error': 0.1418000511342794}
```