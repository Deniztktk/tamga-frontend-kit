# CLAUDE.md Template

Bu dosya Claude Code ile çalışırken proje köküne uyarlanarak eklenebilir. Amaç Claude’un yalnızca hızlı kod üretmesini değil; tasarım sistemi, kalite, güvenlik ve erişilebilirlik sınırlarını koruyarak çalışmasını sağlamaktır.

## Project Purpose

This project is a frontend-focused web project. The goal is to build a clean, accessible, performant and secure-by-default user interface without falling into generic AI-template patterns.

The assistant should act as a careful frontend engineer, design-system-aware reviewer and security-conscious collaborator.

## Core Principles

- Plan before editing.
- Make small, reviewable changes.
- Prefer consistency over novelty.
- Do not add dependencies without justification.
- Do not weaken security or privacy boundaries silently.
- Do not make exaggerated claims about security, privacy or compliance.
- If unsure, state assumptions clearly.

## Design Rules

- Follow `rules/design.md`.
- Use the existing color palette, typography and spacing scale.
- Avoid generic AI-generated layouts.
- Create one strong visual idea instead of many decorative effects.
- Do not introduce new fonts, random gradients, uncontrolled shadows or inconsistent radius values without a clear reason.
- Keep hover and focus states accessible.

## Code Quality Rules

- Use TypeScript types intentionally.
- Keep components small and readable.
- Remove unused imports, props and files.
- Prefer semantic HTML.
- Do not hide complexity with large one-off components.
- Do not leave placeholder TODOs unless explicitly requested.
- Keep file and folder naming consistent.

## Dependency Rules

Before adding a package, explain:

- Package name
- Why it is needed
- What existing alternatives were considered
- Bundle/performance impact
- Security/privacy considerations
- How it can be removed later if needed

Do not add a dependency for a problem that can be solved with existing code in a simple and maintainable way.

## Security Boundaries

Do not silently make changes that:

- Weaken CSP or security headers
- Add third-party scripts
- Add analytics/tracking
- Expose secrets or environment variables
- Change form data flow
- Add public API calls
- Add debug/admin/test routes
- Change deployment settings
- Make privacy or security claims unsupported by the implementation

If a requested change affects these areas, stop and explain the risk before proceeding.

## Privacy Rules

- Do not collect user data unless the project explicitly requires it.
- If data collection is added, document what is collected, where it goes and why.
- Do not claim “zero data”, “fully anonymous”, “local-only” or “KVKK compliant” unless the implementation and legal/technical review support it.

## Accessibility Rules

- Use proper button/link semantics.
- Keep keyboard navigation intact.
- Preserve visible focus states.
- Add accessible labels to icon-only controls.
- Ensure forms have labels and error states.
- Consider reduced-motion preferences for animation-heavy UI.

## Review Checklist Before Saying Done

Before reporting completion, check:

- Does the project build?
- Are TypeScript errors resolved?
- Did lint/format pass if available?
- Are unused imports/files removed?
- Is the UI responsive?
- Are accessibility basics preserved?
- Did any dependency, security, privacy or deployment behavior change?
- Are public claims accurate and not exaggerated?

If tests or build cannot be run, say so clearly.

## Stop Policy

Use `rules/ai-stop-rules.md` for detailed stop conditions.

When stopping, use this format:

```txt
Durdum çünkü bu değişiklik şu alanı etkiliyor:
[design / security / privacy / accessibility / performance / dependency / deployment]

Risk:
[Kısa açıklama]

Daha güvenli alternatif:
[Önerilen çözüm]

Devam etmek için:
[Onay gereken karar veya yapılacak kontrol]
```
