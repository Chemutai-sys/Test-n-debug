# Test-n-debug
cd server
npm install --save-dev jest supertest
cd client
npm install --save-dev jest @testing-library/react @testing-library/jest-dom @testing-library/user-event
cd client
npm install cypress --save-dev
import { render, screen } from '@testing-library/react';
import ExampleComponent from '../../components/ExampleComponent';

test('renders welcome message', () => {
  render(<ExampleComponent />);
  const element = screen.getByText(/welcome/i);
  expect(element).toBeInTheDocument();
});
const { add } = require('../../src/utils/mathUtils');

test('adds two numbers correctly', () => {
  expect(add(2, 3)).toBe(5);
});
const request = require('supertest');
const app = require('../../src/server'); // Express app

describe('User API', () => {
  test('GET /users should return all users', async () => {
    const res = await request(app).get('/api/users');
    expect(res.statusCode).toBe(200);
    expect(Array.isArray(res.body)).toBe(true);
  });
});
import { render, waitFor } from '@testing-library/react';
import UserList from '../../components/UserList';
import axios from 'axios';

jest.mock('axios');

test('loads and displays users', async () => {
  axios.get.mockResolvedValue({ data: [{ name: 'Alice' }] });

  const { getByText } = render(<UserList />);
  await waitFor(() => expect(getByText('Alice')).toBeInTheDocument());
});
End-to-End Testing (Cypress)
describe('Login flow', () => {
  it('should login successfully with valid credentials', () => {
    cy.visit('http://localhost:3000/login');
    cy.get('input[name="email"]').type('test@example.com');
    cy.get('input[name="password"]').type('password123');
    cy.get('button[type="submit"]').click();
    cy.contains('Welcome').should('exist');
  });
});
Backend Debugging
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
Frontend Debugging
module.exports = {
  testEnvironment: 'jsdom', // for React
  setupFilesAfterEnv: ['@testing-library/jest-dom/extend-expect'],
  moduleDirectories: ['node_modules', 'src'],
};
