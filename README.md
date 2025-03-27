# China-Weather-App-
An interactive map application that displays real-time weather conditions for China's ten most populous cities
Project Overview
China Weather App is an interactive map application that displays real-time weather conditions for China's ten most populous cities. Built with Next.js, it provides an intuitive map interface and detailed city information cards, allowing users to easily understand current weather conditions across major cities.

Features
📍 Interactive map showing locations and weather conditions for China's ten most populous cities
🌤️ Real-time weather data that automatically updates every 30 minutes
📊 City card view sorted by population
📱 Responsive design that adapts to various device screens
🔍 Click on map markers to view detailed city and weather information
🏙️ Includes population data and brief descriptions for each city
Technologies Used
Frontend Framework: Next.js 14 (App Router)
Styling: Tailwind CSS, shadcn/ui
Mapping: Leaflet.js, React Leaflet
Data Fetching: WeatherAPI.com
Deployment: Vercel
Installation Guide
Prerequisites
Node.js 18.0.0 or higher
npm, yarn, or pnpm
Steps
1. Clone the zip of repository


2. Install dependencies


```shellscript
npm install
# or
yarn install
# or
pnpm install
```

3. Create environment variables file


Create a `.env.local` file in the project root and add the following:

```plaintext
WEATHER_API_KEY=your_weatherapi_key_here
```

You can get a free API key from [WeatherAPI.com](https://www.weatherapi.com/).

4. Start the development server


```shellscript
npm run dev
# or
yarn dev
# or
pnpm dev
```

5. Open [http://localhost:3000](http://localhost:3000) in your browser


## Deployment

This project can be easily deployed to the Vercel platform:

1. Push your code to a GitHub repository
2. Create a new project on [Vercel](https://vercel.com)
3. Import your GitHub repository
4. Add the environment variable `WEATHER_API_KEY`
5. Click deploy


## Project Structure

```plaintext
china-weather-app/
├── app/                  # Next.js App Router directory
│   ├── api/              # API routes
│   │   └── weather/      # Weather data API endpoint
│   ├── page.tsx          # Main page component
│   └── layout.tsx        # Application layout
├── components/           # React components
│   ├── city-cards.tsx    # City cards component
│   ├── map-client-wrapper.tsx  # Map client wrapper
│   ├── weather-map.tsx   # Weather map component
│   └── ui/               # UI components (shadcn/ui)
├── lib/                  # Utility functions and data
│   └── weather.ts        # Weather data fetching and processing
├── public/               # Static assets
└── README.md             # Project documentation
```

## Key Features Implementation

### Real-time Weather Data

The application fetches weather data from WeatherAPI.com and updates it every 30 minutes both on the server and client side:

```typescript
// Server-side revalidation
const response = await fetch(
  `https://api.weatherapi.com/v1/current.json?key=${apiKey}&q=${city.lat},${city.lon}&aqi=no`,
  { next: { revalidate: 1800 } }, // Cache for 30 minutes
)

// Client-side refresh
const interval = setInterval(
  () => {
    onRefresh()
  },
  30 * 60 * 1000, // Refresh every 30 minutes
)
```

### Interactive Map

The map is implemented using Leaflet.js and React Leaflet, with custom markers for each city showing weather icons:

```typescript
<Marker 
  key={city.name} 
  position={[city.lat, city.lon]} 
  icon={createWeatherIcon(city.icon, city.name)}
>
  <Popup maxWidth={300} minWidth={280}>
    {/* City information */}
  </Popup>
</Marker>
```

## Contribution Guidelines

Contributions are welcome! Feel free to submit a Pull Request or create an Issue.

## License

MIT

## Acknowledgements

- [WeatherAPI.com](https://www.weatherapi.com/) - Weather data provider
- [Leaflet](https://leafletjs.com/) - Open-source interactive maps library
- [Next.js](https://nextjs.org/) - React framework
- [Tailwind CSS](https://tailwindcss.com/) - CSS framework
- [shadcn/ui](https://ui.shadcn.com/) - UI component library



When you deploy your project to GitHub, this README will be displayed on your repository's homepage, providing visitors with their first impression and essential information about your application. If you have actual screenshots of your application, you can replace the placeholder image link to showcase the real appearance of your app.
```
