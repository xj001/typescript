# 更具体的string，number，boolean类型（不知道怎么翻译）

```typescript
type Easy = "easy-in" | "easy-out"
type luckyNumber = 6 | 66 | 8 || 88
interface ValidationSuccess {
  isValid: true;
  reason: null;
}

interface ValidationFailure {
  isValid: false;
  reason: string;
}

type ValidationResult = ValidationSuccess | ValidationFailure;
```

