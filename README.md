# cours-react2
```

import React, { Component } from 'react';
import './App.css';
import Header from './Header';
import Footer from './Footer';

function affiche() {
  alert('hello');
}

const API_URL = 'http://localhost:5000';

class App extends Component {

  getLogin = async () => {
    const headers = { Accept: 'application/json', 'Content-Type': 'application/json' }
    const response = await window.fetch(`${API_URL}/auth`, {
      method: 'POST',
      headers,
      body: {
        username: 'test',
        password: 'testpassword'
      }
    });
    console.log(response);
  }
  render() {
    return (
      <div className="App">
        <Header affiche={affiche} title={'myapp'} />
          <form className="navbar-form navbar-right" role="form">
            <input id="email" type="email" className="form-control" name="email" value="" placeholder="Email Address" />
            <input id="password" type="password" className="form-control" name="password" value="" placeholder="Password" />
            <button type="submit" className="btn btn-primary">Login</button>
          </form>
        <Footer />
      </div>
    );
  }
}

export default App;
