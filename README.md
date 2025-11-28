# AI Dental Receptionist - Landing Page

High-conversion landing page for AI Dental Receptionist SaaS product.

## Features

- Modern, responsive design
- Custom audio player with waveform visualization
- Razorpay payment integration
- QR code generation for demo
- SEO-optimized structure

## Setup

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Environment Variables

1. Copy `.env.example` to `.env.local`
2. Get your Razorpay credentials from [Razorpay Dashboard](https://dashboard.razorpay.com)
3. Add your credentials:

```
RAZORPAY_KEY_ID=rzp_test_xxxxxxxxxxxxx
RAZORPAY_KEY_SECRET=your_razorpay_key_secret_here
```

### 3. Add Demo Audio

Place your demo audio file in the root directory:
- `demo-audio.mp3` (recommended)
- `demo-audio.ogg` (optional, for better browser support)

## Deployment to Vercel

### Option 1: Deploy via Vercel CLI

1. Install Vercel CLI:
```bash
npm i -g vercel
```

2. Login to Vercel:
```bash
vercel login
```

3. Deploy:
```bash
vercel
```

4. Add environment variables in Vercel Dashboard:
   - Go to your project settings
   - Navigate to "Environment Variables"
   - Add `RAZORPAY_KEY_ID` and `RAZORPAY_KEY_SECRET`

### Option 2: Deploy via GitHub

1. Push your code to GitHub
2. Go to [Vercel Dashboard](https://vercel.com)
3. Click "New Project"
4. Import your GitHub repository
5. Add environment variables in project settings
6. Deploy

### Option 3: Deploy via Vercel Dashboard

1. Go to [Vercel Dashboard](https://vercel.com)
2. Click "New Project"
3. Upload your project folder
4. Add environment variables
5. Deploy

## Environment Variables in Vercel

After deployment, add these in Vercel Dashboard → Settings → Environment Variables:

- `RAZORPAY_KEY_ID` - Your Razorpay Key ID
- `RAZORPAY_KEY_SECRET` - Your Razorpay Key Secret

## API Endpoints

### POST /api/verify-payment
Verifies Razorpay payment signature and activates subscription.

**Request Body:**
```json
{
  "razorpay_payment_id": "pay_xxxxx",
  "razorpay_order_id": "order_xxxxx",
  "razorpay_signature": "signature_xxxxx",
  "clinic_name": "Dental Clinic",
  "contact_name": "Dr. John",
  "email": "doctor@clinic.com",
  "phone": "9876543210",
  "plan": "basic",
  "amount": 999
}
```

### POST /api/create-order
Creates a Razorpay order (optional, for better security).

**Request Body:**
```json
{
  "amount": 999,
  "plan": "basic"
}
```

## Next Steps

1. **Database Integration**: Add database to store subscriptions
2. **Email Notifications**: Set up email service (SendGrid, Resend, etc.)
3. **Admin Dashboard**: Create dashboard to manage subscriptions
4. **Analytics**: Add Google Analytics or similar
5. **Custom Domain**: Configure custom domain in Vercel

## Testing

For testing payments, use Razorpay's test mode:
- Test Key ID: Starts with `rzp_test_`
- Test cards: See [Razorpay Test Cards](https://razorpay.com/docs/payments/test-cards/)

## Support

For issues or questions, contact: hello@aidentalreceptionist.com

