## Project Name
BookSelf

## Tagline
My project is an article posting platform featuring a versatile rich text editor built in React, using Next. Js for the frontend and Django for the backend.

## The problem it solves
People can use the platform to efficiently create and publish articles with advanced formatting, media integration, and interactive content through a versatile rich text editor. It streamlines tasks like content management, editing, and real-time previews, making it ideal for bloggers, journalists, and content creators. 

The SEO optimization helps improve search rankings, allowing users to reach a broader audience with minimal effort. Its secure Django backend ensures that all content and data are protected, while the fast, scalable Next. Js frontend delivers a smooth and responsive publishing experience. This combination makes tasks like writing, formatting, and publishing more efficient, safe, and effective for content creators and marketers alike.

## Challenges we ran into
**Frontend:**

We faced several challenges while building the frontend:

- **Monorepo Maintenance:** Initially, maintaining the monorepo structure and keeping everything linked was tricky, especially when defining the project architecture.
- **Next. Js Caching:** Understanding and implementing caching in Next. Js was a bit challenging.
- **Article Editor Features:** Creating the article editor was the most complex part. Implementing tabs was straightforward, but reordering them turned out to be cumbersome. Adjusting font sizes dynamically was also difficult, particularly when the selected text had multiple font sizes; updating them individually was a major hurdle. Editing lists in the document added another layer of complexity. 
- **SEO & Server-Side Rendering:** The most significant challenge was designing the server-side article rendering algorithm using JSON data to ensure the content is search engine indexable.

**Backend:**

Implementing Google authentication and handling article saving and fetching wasn't too difficult compared to the frontend challenges.

## Technologies wee used
- Next.js
- React.js
- Slate.js
- Tailwind CSS 
- Django Rest Framework
- Turborepo
- Git