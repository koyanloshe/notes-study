# Node dependencies 

`npm install --save compression cors helmet`

## // Helmet

`app.use(helmet());`
`app.use(helmet.contentSecurityPolicy({`
`  directives: {`
`    defaultSrc: ["'self'"],`
`    scriptSrc: ["'self'", "'unsafe-inline'"],`
`    styleSrc: ["'self'", "'unsafe-inline'"],`
`    imgSrc: ["'self'", "data:", "*.amazonaws.com"]`
`  }`
`}));`
`app.use(helmet.referrerPolicy({ policy: 'same-origin' }));`

## // Compression

app.use(compress());

## // CORS

app.use(cors());

