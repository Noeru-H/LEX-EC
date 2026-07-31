# LEX-EC: A Lexical Evidence-Channel Audit Framework for Zero-Shot LLM
Personality Classification in Black-Box Settings

This package contains the code used for the experiments reported in
the LEX-EC: A Lexical Evidence-Channel Audit Framework for Zero-Shot LLM
Personality Classification in Black-Box Settings paper and accompanying supplementary material.

## Environment

The notebooks were run with Python 3.14.4.

Install the required packages with:

    pip install -r requirements.txt
    python -m spacy download en_core_web_trf

## Computing infrastructure

Preprocessing, ablation, API orchestration, and statistical analyses were
run on WSL2 on Windows10 using an AMD Ryzen 9 5900X 12-core Processor with 64 GB
of memory. While the system had a CUDA-capable GPU, it was not explicitly used in the experiments. As the LLM vendors are private companies, the provisioned hardware for these is unknown.

The authors note that the main performance bottlenecks were related not to the host system, but waiting for the LLM vendors to return outputs via the API. Please note that a single complete run over all configurations takes several hours.

## Execution order

Run the notebooks in this order:

1. `01-preprocessing.ipynb`
2. `02-text_analysis.ipynb`
3. `03-matched_prediction.ipynb`
4. `04-statistical_analysis.ipynb`

## Data

The experiments use the Pennebaker-King Essays dataset (Pennebaker and King 1999; Celli et al. 2013)  and the myPersonality dataset (Celli et al. 2013), as well as the private student introduction posts dataset, which is not provided due to IRB restrictions. The notebooks expect:

- `essays.csv`
- `mypersonality_final.csv`

These public datasets are provided in this repo for convenience, though please note that they are owned by the authors cited above and we do not claim ownership or copyright.

The student-introduction-post dataset associated code is commented out, but remains for illustrative purposes.

Preprocessing generates, in the root directory:

- `ESSAYS_fullset_text.csv`
- `ESSAYS_fullset_values.csv`
- `ESSAYS_subset_text.csv`
- `ESSAYS_subset_values.csv`
- `FACEBOOK_subset_text.csv`
- `FACEBOOK_subset_values.csv`

## API credentials

The '03-matched_prediction' notebook requires provisioning of:

- `OAI_KEY` (OPENAI_KEY)
- `ANTHROPIC_API_KEY`

## Outputs

Model predictions are saved in:

    personality_outputs/

Evaluation results are saved in:

    evaluation_results/

The prediction notebook checkpoints its output and resumes where it stopped automatically.

## Experimental configuration

- Random seed: 67
- Four prompt conditions
- Five model configurations
- Original and ablated text conditions
- One run per model/prompt/text configuration

Exact prompts, model snapshot identifiers, sampling procedures,
ablation rules, and evaluation metrics are provided in the notebooks, with deeper explanations available in the supplementary material and main paper.

## License

The original code in this repository is released under the MIT License.
Third-party datasets and software dependencies remain subject to their
respective licenses.

## References

- Pennebaker, J. W.; and King, L. A. 1999. Linguistic Styles: Language Use as an Individual Difference. Journal of Personality and Social Psychology, 77(6): 1296–1312.

- Celli, F.; Pianesi, F.; Stillwell, D.; and Kosinski, M. 2013. Workshop on Computational Personality Recognition: Shared Task. Proceedings of the International AAAI Conference on Web and Social Media, 7(2): 2–5.
