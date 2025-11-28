# Deployment Guide - Vercel

## Quick Start

### Step 1: Get Razorpay Credentials

1. Sign up at [Razorpay](https://razorpay.com)
2. Go to Dashboard → Settings → API Keys
3. Generate Test/Live keys
4. Copy your **Key ID** and **Key Secret**

### Step 2: Update Razorpay Key in HTML

Open `index.html` and find line ~598:
```javascript
const RAZORPAY_KEY_ID = 'YOUR_RAZORPAY_KEY_ID';
```

Replace with your actual Key ID:
```javascript
const RAZORPAY_KEY_ID = 'rzp_test_xxxxxxxxxxxxx'; // Your actual key
```

### Step 3: Install Dependencies

```bash
npm install
```

### Step 4: Deploy to Vercel

#### Option A: Using Vercel CLI (Recommended)

```bash
# Install Vercel CLI globally
npm i -g vercel

# Login
vercel login

# Deploy
vercel

# Follow prompts:
# - Set up and deploy? Yes
# - Which scope? Your account
# - Link to existing project? No
# - Project name? ai-dental-receptionist (or your choice)
# - Directory? ./
```

#### Option B: Using GitHub

1. Push code to GitHub:
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/yourusername/ai-dental-receptionist.git
git push -u origin main
```

2. Go to [Vercel Dashboard](https://vercel.com)
3. Click "New Project"
4. Import your GitHub repository
5. Click "Deploy"

### Step 5: Add Environment Variables

After deployment:

1. Go to Vercel Dashboard → Your Project → Settings → Environment Variables
2. Add these variables:

| Variable | Value | Description |
|----------|-------|-------------|
| `RAZORPAY_KEY_ID` | `rzp_test_xxxxx` | Your Razorpay Key ID |
| `RAZORPAY_KEY_SECRET` | `xxxxx` | Your Razorpay Key Secret |

3. **Important**: Redeploy after adding environment variables
   - Go to Deployments tab
   - Click "..." on latest deployment
   - Click "Redeploy"

### Step 6: Add Demo Audio File

1. Record a 15-second demo of your AI receptionist
2. Save as `demo-audio.mp3`
3. Place in the root directory (same folder as `index.html`)
4. Commit and push:
```bash
git add demo-audio.mp3
git commit -m "Add demo audio"
git push
```

Vercel will automatically redeploy.

## Testing Payments

### Test Mode

Use Razorpay test credentials:
- Key ID starts with `rzp_test_`
- Use test cards from [Razorpay Docs](https://razorpay.com/docs/payments/test-cards/)

### Test Cards

| Card Number | CVV | Expiry | Result |
|-------------|-----|--------|--------|
| 4111 1111 1111 1111 | Any | Any future date | Success |
| 5555 5555 5555 4444 | Any | Any future date | Success |
| 5104 0600 0000 0008 | Any | Any future date | Success |

## Custom Domain (Optional)

1. Go to Vercel Dashboard → Your Project → Settings → Domains
2. Add your domain
3. Follow DNS configuration instructions
4. Update CNAME/A records as instructed

## Monitoring

- **Deployments**: Check Vercel Dashboard → Deployments
- **Logs**: Vercel Dashboard → Your Project → Functions → View logs
- **Analytics**: Add Google Analytics or Vercel Analytics

## Troubleshooting

### Payment verification fails
- Check environment variables are set correctly
- Verify `RAZORPAY_KEY_SECRET` matches your Razorpay dashboard
- Check Vercel function logs for errors

### API endpoint not found
- Ensure `api/verify-payment.js` exists
- Check `vercel.json` configuration
- Verify deployment includes the `api` folder

### Audio not playing
- Check file path: `demo-audio.mp3` in root directory
- Verify file is committed to repository
- Check browser console for errors

## Next Steps

1. **Database**: Add database (MongoDB, PostgreSQL) to store subscriptions
2. **Email**: Set up email service (SendGrid, Resend) for confirmations
3. **Analytics**: Add Google Analytics or Plausible
4. **Monitoring**: Set up error tracking (Sentry)
5. **Backup**: Regular backups of subscription data

## Support

For issues:
- Check Vercel [Documentation](https://vercel.com/docs)
- Check Razorpay [Documentation](https://razorpay.com/docs)
- Contact: hello@aidentalreceptionist.com

