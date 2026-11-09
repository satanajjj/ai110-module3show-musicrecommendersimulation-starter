# 🎵 Music Recommender Simulation

## Project Summary

In this project you will build and explain a small music recommender system.

Your goal is to:

- Represent songs and a user "taste profile" as data
- Design a scoring rule that turns that data into recommendations
- Evaluate what your system gets right and wrong
- Reflect on how this mirrors real world AI recommenders

Replace this paragraph with your own summary of what your version does.

---

## How The System Works

Explain your design in plain language.

Some prompts to answer:

- What features does each `Song` use in your system
  - For example: genre, mood, energy, tempo
- What information does your `UserProfile` store
- How does your `Recommender` compute a score for each song
- How do you choose which songs to recommend

Each Song is scored using its genre, mood, and energy. The UserProfile stores the user’s favorite genre, favorite mood, target energy, and whether they like acoustic music, though acoustic preference is not yet included in scoring.

The Recommender awards 40% for a matching genre, 25% for a matching mood, and up to 35% for energy closeness. Songs closer to the user’s target energy earn more points.

Songs are ranked by their total score, and the highest-scoring songs are recommended.

Algo recipe:
1. Read the taste profile: favorite genre "lofi", favorite mood "chill", and target energy 0.4.
2. Score each song:
   - Add 0.40 points if its genre matches.
   - Add 0.25 points if its mood matches.
   - Add 0.35 × (1 − |song energy − target energy|) to reward energy closeness.
3. Rank the songs from highest to lowest total score. Scores range from 0 to 1. Break ties using the song’s ID, lowest first.
4. Recommend the top five songs, or all songs if fewer than five are available.
5. Explain each recommendation by reporting genre and mood matches and how close its energy is to the target.

This recipe may favor songs in the user’s preferred genre because genre matches earn twice as many points as mood matches, limiting discovery of other genres. Genres with more songs in the dataset may also dominate recommendations. Mood labels are subjective, and energy alone may not fully capture how a song feels to different listeners.

---

## Getting Started

### Setup

1. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # Mac or Linux
   .venv\Scripts\activate         # Windows

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Run the app:

```bash
python -m src.main
```

### Running Tests

Run the starter tests with:

```bash
pytest
```

You can add more tests in `tests/test_recommender.py`.

---

## Sample Recommendation Output

Paste a sample of your recommender's output here as a text block so a reader can see what it produces:

```
# e.g.:
# User profile: genre=indie, mood=chill, energy=low
# Recommendations:
#   1. ...
#   2. ...
#   3. ...
```

**Screenshot or video** *(optional)*: <!-- Insert a screenshot or demo video link here -->

---

## Experiments You Tried

Use this section to document the experiments you ran. For example:

- What happened when you changed the weight on genre from 2.0 to 0.5
- What happened when you added tempo or valence to the score
- How did your system behave for different types of users

---

## Limitations and Risks

Summarize some limitations of your recommender.

Examples:

- It only works on a tiny catalog
- It does not understand lyrics or language
- It might over favor one genre or mood

You will go deeper on this in your model card.

---

## Reflection

Read and complete `model_card.md`:

[**Model Card**](model_card.md)

Write 1 to 2 paragraphs here about what you learned:

- about how recommenders turn data into predictions
- about where bias or unfairness could show up in systems like this



