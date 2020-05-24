# When __dirname__

`import path from 'path';`

`const root = path.join(__dirname, '../../');`

`app.use('/', express.static(path.join(root, 'dist/client')));`
`app.use('/uploads', express.static(path.join(root, 'uploads')));`
`app.get('/', (req, res) => {`
`  res.sendFile(path.join(root, '/dist/client/index.html'));`
`});`

