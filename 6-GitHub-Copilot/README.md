# 6. GitHub Copilot & AI-Assisted Code Generation

[![Software Engineering](https://img.shields.io/badge/Course-Software%20Engineering%20(UE24CS351AA2)-0052CC.svg)](https://pes.edu)
[![Student SRN](https://img.shields.io/badge/SRN-PES1UG24CS453-orange.svg)](https://github.com/siasimran-magic)
[![AI Pair Programming](https://img.shields.io/badge/GitHub-Copilot%20Enabled-8A2BE2.svg)](https://github.com/features/copilot)

**Project**: Online Internship & Placement Preparation Portal (IPP)  
**Institution**: PES University | Department of Computer Science & Engineering  
**Student SRN**: PES1UG24CS453  
**Official Repository Link**: [https://github.com/siasimran-magic/InternshipPlacementPortal_IPP](https://github.com/siasimran-magic/InternshipPlacementPortal_IPP)

---

## 🤖 1. Overview of AI Pair Programming Workflow

GitHub Copilot was leveraged as an AI pair programmer throughout the development lifecycle of the **Online Internship & Placement Preparation Portal (IPP)**. The objective was to accelerate implementation, generate robust test fixtures, enforce type safety, and scaffold complex algorithmic calculations (such as weighted readiness percentiles and countdown timers).

---

## 💡 2. Prompt Engineering Strategies & Generated Code Samples

### Case Study 1: Timed Aptitude Exam Countdown & Auto-Submit Hook
* **Developer Prompt**:
  > *"Write a custom React hook `useExamTimer` that accepts a total duration in seconds and an `onTimeUp` callback. It must decrement every second, persist state to sessionStorage to prevent timer reset on page reload, trigger a warning when under 5 minutes remain, and automatically invoke `onTimeUp` when time hits 0."*

* **GitHub Copilot Synthesis**:
```javascript
import { useState, useEffect, useRef } from 'react';

export function useExamTimer(initialSeconds, onTimeUp) {
  const [secondsLeft, setSecondsLeft] = useState(() => {
    const saved = sessionStorage.getItem('exam_seconds_left');
    return saved !== null ? parseInt(saved, 10) : initialSeconds;
  });

  const onTimeUpRef = useRef(onTimeUp);
  useEffect(() => {
    onTimeUpRef.current = onTimeUp;
  }, [onTimeUp]);

  useEffect(() => {
    if (secondsLeft <= 0) {
      sessionStorage.removeItem('exam_seconds_left');
      if (onTimeUpRef.current) onTimeUpRef.current();
      return;
    }

    const intervalId = setInterval(() => {
      setSecondsLeft((prev) => {
        const nextValue = prev - 1;
        sessionStorage.setItem('exam_seconds_left', nextValue.toString());
        return nextValue;
      });
    }, 1000);

    return () => clearInterval(intervalId);
  }, [secondsLeft]);

  const isLowTime = secondsLeft > 0 && secondsLeft <= 300; // Under 5 mins
  const formatTime = () => {
    const mins = Math.floor(secondsLeft / 60).toString().padStart(2, '0');
    const secs = (secondsLeft % 60).toString().padStart(2, '0');
    return `${mins}:${secs}`;
  };

  return { secondsLeft, isLowTime, formattedTime: formatTime() };
}
```

---

### Case Study 2: Weighted Employability Readiness Score Aggregator
* **Developer Prompt**:
  > *"Create a Python service function `calculate_readiness_score` that takes a student's mock exam scores categorized by Quantitative (30%), Logical Reasoning (25%), Verbal Ability (15%), and Core Technical (30%). It should compute the normalized weighted readiness score out of 100, identify the student's weakest domain, and recommend targeted practice."*

* **GitHub Copilot Synthesis**:
```python
from typing import Dict, Any

DOMAIN_WEIGHTS = {
    "quantitative": 0.30,
    "logical": 0.25,
    "verbal": 0.15,
    "technical": 0.30
}

def calculate_readiness_score(domain_scores: Dict[str, float]) -> Dict[str, Any]:
    """
    Computes overall employability readiness index and pinpoints focus domains.
    domain_scores: percentage scores (0.0 to 100.0) per domain.
    """
    total_weighted_score = 0.0
    weakest_domain = None
    min_score = float('inf')

    for domain, weight in DOMAIN_WEIGHTS.items():
        score = domain_scores.get(domain, 0.0)
        total_weighted_score += score * weight
        if score < min_score:
            min_score = score
            weakest_domain = domain

    readiness_index = round(total_weighted_score, 2)
    
    # Recommendation logic
    recommendations = {
        "quantitative": "Revise Time-Speed-Distance and Permutations/Combinations.",
        "logical": "Practice seating arrangements and syllogisms.",
        "verbal": "Work on reading comprehension and critical reasoning passages.",
        "technical": "Reinforce Data Structures (Trees, Graphs) and OS concepts (Paging, Deadlocks)."
    }

    return {
        "readiness_index": readiness_index,
        "performance_bracket": "High" if readiness_index >= 75 else "Moderate" if readiness_index >= 50 else "Needs Improvement",
        "weakest_domain": weakest_domain,
        "recommendation": recommendations.get(weakest_domain, "Continue regular practice.")
    }
```

---

## 📸 3. Evidence & Screenshots

Place captured screenshots demonstrating GitHub Copilot interactions in the `screenshots/` directory:
* `screenshots/copilot_timer_generation.png`: Inline Copilot completion showing generation of `useExamTimer`.
* `screenshots/copilot_chat_readiness.png`: Copilot Chat conversation refining the readiness algorithm.
* `screenshots/copilot_test_generation.png`: Automated test case generation for edge-case handling.
