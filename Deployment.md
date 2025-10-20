### Apify Platform

- [Apify SDK Documentation](https://docs.apify.com/sdk/js) - Build your own Actors
- [Apify Academy](https://docs.apify.com/academy) - Learn web scraping
- [Integrations](https://apify.com/integrations) - Connect with 1000+ apps
- [Discord Community](https://discord.com/invite/jyEM2PRvMU) - Get help and support

## Development & Usage

### Running the Actor

#### Option 1: Apify Console (Recommended)

1. Visit the [Actor page](https://console.apify.com/actors)
2. Click **"Try for free"** or add to your account
3. Configure input parameters
4. Click **"Start"** to run

#### Option 2: Local Development

```bash
# Clone the repository
git clone <repository-url>
cd clearbit-combined

# Install dependencies
npm install

# Configure input in storage/key_value_stores/default/INPUT.json
# Run the Actor
apify run

# Run with custom input
apify run --input='{"tombaApiKey":"ta_xxx","tombaApiSecret":"ts_xxx","emails":[""]}'
```

#### Option 3: Apify CLI

```bash
# Install Apify CLI
npm install -g apify-cli

# Run directly from Apify Store
apify call <actor-name> --input='{"tombaApiKey":"ta_xxx","tombaApiSecret":"ts_xxx","emails":[""]}'
```

## Deployment Options

### Deploy from Local Machine

```bash
# Login to Apify
apify login

# Deploy your Actor
apify push
```

### Deploy from Git Repository

1. Go to [Actor Creation Page](https://console.apify.com/actors/new)
2. Click **"Link Git Repository"**
3. Connect your GitHub/GitLab repository
4. Configure build settings
5. Deploy automatically on commits

## Important Notes

### API Key Security

- **Never** commit API keys to version control
- Use Apify's secret input fields for credentials
- Store keys securely in environment variables for local development

### Rate Limiting

- Tomba limits to **150 requests per minute**
- Actor automatically handles rate limiting with delays
- Large batches may take time to complete

### Cost Considerations

- Each domain processed = 1 Tomba API request
- Monitor your Tomba usage dashboard
- Consider Tomba's pricing tiers for volume usage

## Technical Details

- **Runtime**: Node.js 18+
- **Dependencies**: Apify SDK v3, Tomba SDK v1
- **Memory**: 1024MB recommended
- **Timeout**: 3600 seconds for large batches

## Support

- **Issues**: [GitHub Issues](https://github.com/your-repo/issues)
- **Community**: [Apify Discord](https://discord.com/invite/jyEM2PRvMU)
- **Contact**: [Apify Support](https://apify.com/support)

## License

This project is licensed under the ISC License - see the LICENSE file for details.

---

**Made with ❤️ by the Apify community** | **Powered by [Tomba API](https://tomba.io)**
