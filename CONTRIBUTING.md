# Contributing to AURA

Thank you for your interest in contributing to AURA! 🎙️

## Ways to Contribute

- 🐛 **Bug Reports** — Open an issue with steps to reproduce
- 💡 **Feature Requests** — Suggest new voice commands or integrations
- 🔧 **Code Contributions** — Fix bugs, add action handlers, improve NLU
- 📖 **Documentation** — Improve the README or add inline docstrings

## Getting Started

1. **Fork** the repository
2. **Clone** your fork:
   ```bash
   git clone https://github.com/YOUR_USERNAME/AURA-AI-Voice-Assistant-.git
   ```
3. **Set up** the environment:
   ```bash
   python -m venv .venv
   .venv\Scripts\Activate.ps1
   pip install -r requirements.txt
   ```
4. **Configure** your `.env` with a valid `GROQ_API_KEY`
5. **Run** in dev mode:
   ```bash
   python app.py --bypass-auth
   ```

## Adding a New Voice Command (Action Handler)

1. Create your handler in `actions/your_action.py`:
   ```python
   from core.action_registry import registry
   from core.result_types import ParsedCommand, ExecutionResult

   def handle_my_action(cmd: ParsedCommand) -> ExecutionResult:
       # Your logic here
       return ExecutionResult(success=True, message="Done!")

   registry.register("my_intent", "my_action", handle_my_action)
   ```
2. Add your intent + keywords to `config/synonym_map.json`
3. If needed, add slot extraction logic in `brain/core/slot_extractor.py`
4. Test it with `python app.py --bypass-auth`

## Pull Request Guidelines

- Create a feature branch: `git checkout -b feature/my-feature`
- Keep commits atomic and descriptive
- Test your changes before submitting
- Open a PR against the `main` branch with a clear description

## Code Style

- Follow **PEP 8** for Python
- Use **type hints** on all function signatures
- Add **docstrings** to new classes and public methods
- Use **loguru** for all logging (`from loguru import logger`)
