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

  constructor(props, context) {
    super(props, context);
    this.state = {
      email: ''
    };
    this.onChangeEmail = this.onChangeEmail.bind(this);
    this.onChangePassword = this.onChangePassword.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }
  getLogin = async (email, password) => {
    const headers = { Accept: 'application/json', 'Content-Type': 'application/json' }
    const response = await window.fetch(`${API_URL}/auth`, {
      method: 'POST',
      headers,
      body: { email, password }
    });
    console.log(response);
  }

  onChangeEmail = (event) => {
    this.setState({ email: event.target.value });
  }

  onChangePassword = (event) => {
    this.setState({ password: event.target.value });
  }

  handleSubmit = (event) => {
    event.preventDefault();
    this.getLogin({ email: this.state.email, password: this.state.password });
    // console.log(this.state);
  }

  render() {
    return (
      <div className="App">
        <Header affiche={affiche} title={'myapp'} />
          <form onSubmit={this.handleSubmit} className="navbar-form navbar-right" role="form">
            <input value={this.state.email} onChange={this.onChangeEmail} id="email" type="email" />
            <input value={this.state.password} onChange={this.onChangePassword} id="password" type="password" className="form-control" name="password" placeholder="Password" />
            <button type="submit" className="btn btn-primary">Login</button>
          </form>
          {this.state.email}
        <Footer />
      </div>
    );
  }
}

export default App;
```
