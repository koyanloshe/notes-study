# Testing a component with fake data

Above the app class paste

const posts = [{
  id: 2,
  text: 'Lorem ipsum',
  user: {
    avatar: '/uploads/avatar1.png',
    username: 'Test User'
  }
},
{
  id: 1,
  text: 'Lorem ipsum',
  user: {
    avatar: '/uploads/avatar2.png',
    username: 'Test User 2'
  }
}];

In the render function pass

const { posts } = this.state;

return (
  <div className="container">
    <div className="feed">
      {posts.map((post, i) => 
        <div key={post.id} className="post">
          <div className="header">
            <img src={post.user.avatar} />
            <h2>{post.user.username}</h2>
          </div>
          <p className="content">
            {post.text}
          </p>
        </div>
      )}
    </div>
  </div>
)

At the top of the App class
state = {
  posts: posts
}

Which is the same as 
constructor(props) {
  super(props);

  this.state = {
    posts: posts
  };
}

## CSS config in webpack

Check that this block is in the webpack.client.config.js

{
  test: /\.css$/,
  use: ['style-loader', 'css-loader'],
},

Place styles.css file in /assets/css/

Add import instruction to app.js

import '../../assets/css/style.css';

