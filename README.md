# Agentic Career Conversation

An AI-powered conversational agent that represents **Kenneth Pieterson** on his personal website. The bot engages professionally with visitors, shares career insights, and captures leads through email collection and question logging.

## Features

- **Professional Persona**: Maintains Kenneth Pieterson's professional voice and expertise
- **Dynamic Knowledge Base**: Uses LinkedIn profile and career summary for contextual responses  
- **Lead Capture**: Prompts for and records visitor email addresses
- **Question Logging**: Tracks unanswered questions for follow-up and improvement
- **Real-time Notifications**: Sends push notifications via Pushover API
- **Web Interface**: Clean, responsive chat interface built with Gradio

## Quick Start

### Prerequisites

- Python 3.8+
- OpenAI API account and key
- Pushover account and API credentials

### Installation

1. **Clone and setup**:
```bash
git clone <repository-url>
cd agentic-career-conversation
pip install -r requirements.txt
```

2. **Create required directories and files**:
```bash
mkdir me
# Add your Profile.pdf and summary.txt to the me/ directory
```

3. **Environment Configuration**:
Create a `.env` file in the project root:
```env
# OpenAI Configuration
OPENAI_API_KEY=your_openai_api_key_here

# Pushover Configuration  
PUSHOVER_TOKEN=your_pushover_app_token
PUSHOVER_USER=your_pushover_user_key
```

4. **Prepare Content Files**:
   - `me/Profile.pdf`: Your LinkedIn profile exported as PDF
   - `me/summary.txt`: Career summary and key background information

5. **Run the Application**:
```bash
python agent.py
```

The Gradio interface will launch in your browser at `http://127.0.0.1:7860`

## Dependencies

Install all required packages:
```bash
pip install openai python-dotenv pypdf requests gradio
```

Or create a `requirements.txt`:
```
openai>=1.0.0
python-dotenv>=1.0.0
pypdf>=3.0.0
requests>=2.28.0
gradio>=4.0.0
```

## Project Structure

```
agentic-career-conversation/
├── agent.py              # Main application file
├── .env                  # Environment variables (create this)
├── requirements.txt      # Python dependencies
├── me/
│   ├── Profile.pdf      # LinkedIn profile PDF
│   └── summary.txt      # Career summary text
└── README.md
```

## Configuration

### OpenAI API
- Sign up at [OpenAI Platform](https://platform.openai.com)
- Generate an API key from your dashboard
- Ensure you have credits/billing configured

### Pushover Setup
- Create account at [Pushover.net](https://pushover.net)
- Create a new application to get your `PUSHOVER_TOKEN`
- Find your user key (`PUSHOVER_USER`) in account settings

## How It Works

1. **Initialization**: Loads Kenneth's profile data and creates AI persona
2. **User Interaction**: Visitors chat through Gradio web interface
3. **AI Processing**: OpenAI processes messages with Kenneth's context
4. **Tool Execution**: Uses function calling for email capture and question logging
5. **Notifications**: Sends real-time alerts via Pushover for important interactions

## Core Functions

- `record_user_details()`: Captures visitor email and contact information
- `record_unknown_question()`: Logs questions the AI couldn't answer
- `push()`: Sends notifications via Pushover API
- `Me.chat()`: Main conversation handler with tool integration

## Customization

To adapt for different personas:

1. Update the `name` variable in the `Me` class
2. Replace content in `me/Profile.pdf` and `me/summary.txt`
3. Modify the system prompt in `system_prompt()` method
4. Adjust tool functions as needed

## Troubleshooting

### Common Issues

**"No module named 'openai'"**
- Run: `pip install -r requirements.txt`

**"FileNotFoundError: Profile.pdf"** 
- Ensure `me/Profile.pdf` and `me/summary.txt` exist
- Check file paths and permissions

**"OpenAI API Error"**
- Verify `OPENAI_API_KEY` in `.env` file
- Check API key validity and billing status
- Ensure model access (gpt-4o-mini)

**"Pushover delivery failed"**
- Verify `PUSHOVER_TOKEN` and `PUSHOVER_USER` values
- Test credentials at pushover.net

**Interface won't load**
- Check if port 7860 is available
- Try: `python agent.py --server-port 8080`

### Debug Mode

Add debugging to `agent.py`:
```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

## Security Notes

- Keep `.env` file private and never commit to version control
- Add `.env` to your `.gitignore` file
- Regularly rotate API keys
- Monitor API usage and costs

## License

[Specify your license here]

## Contributing

[Add contribution guidelines if applicable]
