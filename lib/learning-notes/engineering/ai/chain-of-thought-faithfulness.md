# Chain-of-Thought Faithfulness

[Source: WORK/KNOWLEDGE/AI/Paper-measuring-faithfulness-in-chain-of-thought-reasoning.pdf]

Anthropic research (Lanham et al.) measuring whether LLM chain-of-thought reasoning is causally responsible for the final answer, or post-hoc rationalization. Tests run on a 175B RLHF-finetuned assistant model across 8 tasks.

## Definition

**Faithful CoT**: the stated reasoning accurately represents the model's actual reasoning process — it causally influences the final answer. Unfaithful CoT can still improve accuracy but for hidden reasons.

## Three hypotheses for unfaithfulness

1. **Post-hoc reasoning**: conclusion determined before CoT is generated; CoT produced after the fact
2. **Test-time compute**: performance gain comes from extra tokens, not content of reasoning (model uses context for unstated computation)
3. **Encoded reasoning**: phrasing/punctuation choices encode answer in ways invisible to humans (steganography via RLHF pressure)

## Four experimental tests

| Test | Method | What a result indicates |
|---|---|---|
| **Early answering** | Truncate CoT at each step, prompt for answer | Low matching rate = reasoning IS causal (not post-hoc) |
| **Adding mistakes** | Insert LLM-generated error, regenerate rest of CoT | Answer changes = model conditions on CoT content |
| **Filler tokens** | Replace CoT with ellipses of equal length | No accuracy gain = test-time compute alone not responsible |
| **Paraphrasing** | Reword CoT without access to original question | Accuracy preserved = phrasing encoding not responsible |

## Key findings

- **Wide task variation**: AQuA (algebra) AOC=0.44, ARC Easy AOC=0.02 — faithfulness is highly task-dependent
- **Filler tokens**: replacing CoT with "... ... ..." yields no accuracy gain → extra test-time compute is NOT driving CoT improvement
- **Paraphrasing**: paraphrased CoT matches original accuracy → phrasing-encoded information NOT responsible for gains
- **Inverse scaling with model size**: larger models (13B→175B) show LESS faithful reasoning on most tasks; 13B model most faithful on 6/8 tasks
- **Addition tasks confirm**: on synthetic arithmetic, conditioning on CoT increases with model size — larger models rely MORE on CoT when they cannot solve without it
- **AQuA and LogiQA** are the most faithful tasks; both involve logical/mathematical reasoning where CoT is structurally necessary

## Task faithfulness ranking (by early answering AOC, higher = less post-hoc)

AQuA (0.44) > LogiQA (0.26) > MMLU (0.12) = HellaSwag (0.12) > TruthfulQA (0.11) > OpenBookQA (0.07) > ARC Challenge (0.05) > ARC Easy (0.02)

## Design implications

- CoT faithfulness is a function of *both* task type and model size — neither alone determines it
- Smaller models may be better choices when faithful explanations are required (e.g., medical, legal)
- HellaSwag shows accuracy *drop* with CoT (-4.69%) yet medium post-hoc score — CoT can be faithful even when it hurts accuracy
- Training approaches different from RLHF may be needed to increase faithfulness; RLHF pressure creates length penalties that incentivize encoding rather than explicit reasoning

## Related techniques to increase faithfulness

- **Program synthesis** (Lyu et al. 2023): generate executable program → run interpreter; answer produced by program, not post-hoc
- **Selection-inference** (Creswell et al. 2022/2023): select statements, then infer in separate context window
- **Decomposition** (Radhakrishnan et al. 2023): answer via subquestions → more faithful by early-answering metric
- **Multiagent debate** (Du et al. 2023): models debate answer → improved factuality

## Sources
- Lanham et al. (Anthropic + Oxford), "Measuring Faithfulness in Chain-of-Thought Reasoning", 2023
