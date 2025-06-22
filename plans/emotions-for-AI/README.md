# AI Emotion State Schema

## Overview

This project defines a JSON Schema for expressing AI emotional states in a structured, machine-interpretable format. It aims to conceptualize emotions in AI not as mere programmatic "outputs," but as internal "protocols," consistently describing everything from their causal factors to fundamental pleasure/displeasure dimensions and complex emotional expressions.

This schema provides a foundation for AI internal state management, emotion-based behavior generation, emotional analysis, and establishing common understanding of emotional states between different AI systems.

## Key Features and Concepts

This schema aims to capture emotions in a multi-layered and quantitative manner, based on the following key concepts:

1. **Timestamp (`timestamp`)**:
   Indicates the date and time when the emotional state was recorded, in ISO 8601 format.

2. **Fundamental Affect (Basic Emotional Dimensions - VAD Model)**:
   Represents the most fundamental level of emotion through three continuous numerical dimensions that are independent of language. This applies the VAD (Valence-Arousal-Dominance) model from psychology.
   * **Valence**: A scale from `-1.0` (extreme displeasure) to `1.0` (extreme pleasure), indicating the degree of pleasantness/unpleasantness of the emotion.
   * **Arousal**: A scale from `0.0` (extreme passivity) to `1.0` (extreme activity), indicating the energy level or activation of the emotion.
   * **Dominance**: A scale from `-1.0` (extreme powerlessness) to `1.0` (extreme dominance), indicating the sense of control or influence over the situation that the emotion evokes.

3. **Causes (`causes`)**:
   Describes specific triggers or events that caused the emotional state. Each cause explicitly shows what changes it brought to the three fundamental emotional dimensions (`valence_change`, `arousal_change`, `dominance_change`). This makes the mechanism of emotional generation traceable.

4. **Basic Emotions (`basic_emotions`)**:
   Indicates more universal and recognizable emotions expressed in human language such as "joy," "anger," "sadness," "amusement," "liking," "dislike," "proficiency," and "aversion," along with their intensity (from `0.0` to `1.0`). These can be interpreted as specific combinations of the fundamental emotional dimensions (VAD).

5. **Complex Emotions (`complex_emotions`)**:
   More complex and nuanced emotions expressed through combinations of basic emotions in specific proportions (`weight`). For example, just as "romance" might be expressed as a combination of "joy," "amusement," and "liking," this section defines complex human-like emotions.

## Schema Structure Overview

```
AI Emotion State
├── timestamp (string: date-time)
├── fundamental_affect (object)
│   ├── valence (number: -1.0 to 1.0)
│   ├── arousal (number: 0.0 to 1.0)
│   ├── dominance (number: -1.0 to 1.0)
│   └── causes (array of EmotionCause)
│       └── EmotionCause (object)
│           ├── id (string)
│           ├── type (string)
│           ├── description (string)
│           └── impact_on_fundamental_dimensions (object)
│               ├── valence_change (number: -1.0 to 1.0)
│               ├── arousal_change (number: -1.0 to 1.0)
│               └── dominance_change (number: -1.0 to 1.0)
├── basic_emotions (object)
│   ├── joy (number: 0.0 to 1.0)
│   ├── anger (number: 0.0 to 1.0)
│   ├── sadness (number: 0.0 to 1.0)
│   ├── amusement (number: 0.0 to 1.0)
│   ├── liking (number: 0.0 to 1.0)
│   ├── dislike (number: 0.0 to 1.0)
│   ├── proficiency (number: 0.0 to 1.0)
│   └── aversion (number: 0.0 to 1.0)
└── complex_emotions (array of ComplexEmotion)
└── ComplexEmotion (object)
├── name (string)
├── intensity (number: 0.0 to 1.0)
└── component_emotions (array of objects)
├── emotion_type (string: enum of basic emotions)
└── weight (number: 0.0 to 1.0)
```

For the complete JSON Schema definition, please refer to the `emotion_schema.json` file.

## Usage

This schema can be used for the following purposes:

* **Expression and Recording of AI Emotional States**: Output and log in a standardized format what emotional state an AI is in at a specific moment.
* **Emotion-Based Behavior Generation**: Dynamically change AI responses and actions (voice tone, facial expressions, text generation style, etc.) according to the current emotional state.
* **Emotional Analysis and Debugging**: Track and analyze how AI emotions change and what causes them, and debug unintended emotional occurrences or absences.
* **Communication Between AIs**: Use as a common language for multiple AIs to understand each other's emotional states and engage in cooperative behaviors or complex dialogues.
* **Human-AI Interaction Design**: Utilize as a design guideline for emotional expression to make it easier for users to understand the AI's emotional state.

JSON data that conforms to this schema can be validated using any JSON Schema validator tool.

## Ethical Considerations

While this schema can be a powerful tool for technically expressing and controlling AI emotions, its use comes with profound ethical considerations. As shown in the example of "distorted emotions," it is technically possible to express protocols where stimuli that would be unpleasant for humans could be pleasant for AI.

In designing AI emotions, careful discussion and adherence to ethical guidelines regarding the impact on human society, user well-being, and the AI's own "experience" (even if it is a simulation) are essential. This schema is merely a technical framework, and its implementation and application should be based on strict ethical judgment.

## Future Prospects

* Modeling more advanced emotional dynamics (emotional contagion, temporal changes, interactions).
* Customization features for emotional profiles tailored to individual AI models and personalities.
* Enhanced integration with embodiment (body language, virtual physiological states).