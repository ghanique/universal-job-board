# Universal Job Board

A job board designed to focus on core skills over specific platform experience, eliminating biases like ageism, and fostering direct communication between job posters and applicants. This repository serves as the foundation for an open, schema-driven platform with GraphQL APIs for seamless integration.

## Purpose

This project aims to:

1. Provide a transparent and bias-free job board where companies and applicants can connect directly without middlemen.
2. Focus on **core skills and design patterns** rather than specific frameworks or cloud platforms.
3. Standardize job and applicant data through robust schemas, enabling powerful and flexible GraphQL APIs for querying and integration.
4. Encourage cross-platform and framework-agnostic thinking.

## Features

- **Fixed Schemas** for applicants and job postings to ensure consistency.
- Focus on **core skills** (e.g., cloud computing concepts, design patterns) over specific tool experience.
- **GraphQL API** for seamless data querying and filtering.
- Support for **component-based architecture** in frontend frameworks (React, Vue, Angular, etc.) and **platform-agnostic cloud computing skills** (AWS, Azure, GCP).

## Next Steps

1. Implement the `ats.graphql` schema and resolvers.
2. Create the `atsService.js` to handle:
   - Workflow management.
   - Candidate matching logic (e.g., comparing `skills`).
3. Build a basic front-end component (`ATSDashboard.vue`) to manage the applicant pipeline.
4. Document the workflow for contributing to ATS-specific features.

Let me know if you'd like help setting up any specific files or parts of the ATS!

## Schemas

### Applicant Schema

```graphql
type Applicant {
  id: ID!
  name: String!
  location: String
  contactInfo: ContactInfo!
  skills: [String!]!
  experience: [Experience!]
  education: [Education!]
  certifications: [String]
  portfolio: [Portfolio!]
  references: [Reference]
  availability: Availability
}

type ContactInfo {
  email: String!
  phone: String
  linkedIn: String
  github: String
  website: String
}

type Experience {
  role: String!
  company: String!
  responsibilities: [String!]
  technologies: [String]
}

type Education {
  degree: String
  field: String
  institution: String
}

type Portfolio {
  title: String
  url: String
  description: String
}

type Reference {
  name: String
  contact: String
  relationship: String
}

type Availability {
  remote: Boolean
  relocation: Boolean
  hoursPerWeek: Int
}
```
