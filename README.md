# Serverless Backend

## Backend

### What is Backend?

Backend refers to the server-side processes that manage the logic, database interactions, and overall functionality of web applications, which users do not see. You might have used Express to create the backend server. The way the server usually runs is by using the command `node index.js`, which starts a process on a certain port (e.g., 8000).

To make the backend accessible to others, you need to deploy it on a server. There are various ways to deploy your application on the internet:

### Cloud Computing Platforms

These platforms allow you to rent a virtual machine and deploy your application. (Running it on your laptop is an option, but it won’t be available 24/7.) Examples include:

- AWS
- Azure
- Cloudflare

### Considerations for Cloud Deployment

When deploying your application on the cloud, you need to:

- Take care of how and when to scale.
- Manage base costs (even if no one is visiting the app).

## Serverless Backend

![Serverless Backend](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3841a92-a773-4ae2-b373-52b87f954981/199d28ea-eae2-4e37-856d-0ab1c1ca460f/image.png)

Serverless backend works similarly to pushing code to GitHub. Platforms like Vercel automatically deploy the application on the internet. 

You just need to write the backend code and run a command to deploy the app. Serverless platforms offer features like auto-scaling and charging per request, making it more cost-effective than renting a virtual machine. 

However, some challenges include higher costs at scale and the cold start problem.

## Serverless Providers

- AWS Lambda
- Google Cloud Functions
- Cloudflare Workers (We will use this to deploy our app as it doesn’t require a credit card.)

## Cloudflare Worker Setup

📌 **Sign up**: [https://www.cloudflare.com/](https://www.cloudflare.com/)

💡 **Learn more about Cloudflare Workers**:

- [YouTube Tutorial](https://www.youtube.com/watch?v=H7Qe96fqg1M)
- [Cloudflare Workers Documentation](https://developers.cloudflare.com/workers/reference/how-workers-works/)

### Key Points

- **Cloudflare Workers do not use the Node.js runtime.** Instead, they have their own runtime.

### What is Node.js?

Node.js is a runtime environment that allows JavaScript to be executed on your local machine. It is built on Chrome's V8 JavaScript engine, which compiles JavaScript into machine code.

Read more: [Why Cloudflare Workers don’t use Node.js](https://www.perplexity.ai/search/cloudflare-workers-dont-use-th-DDU7e_8GRyOwlFFQ3pptKA)

### Try a Test Worker

1. Create a test worker from the UI ([Cloudflare Dashboard](https://dash.cloudflare.com/78a4b68097082fdbfdba1f6506ee93b8/workers-and-pages/create)).
2. Deploy it and try hitting the generated URL.

![Test Worker](https://img.notionusercontent.com/s3/prod-files-secure%2Fc3841a92-a773-4ae2-b373-52b87f954981%2Ffd4edd6d-008c-4102-b674-c29b8c0f5042%2Fimage.png/size/w=2000?exp=1737298269&sig=L-KCOGqHwvmeJnCxr84pCla0vXgvbEz2vIRA0rpLXco)

## Initializing a Worker

### Steps to Initialize

1. **Create a worker**

    ```bash
    npm create cloudflare -- serverless-backend
    
    // Select "No" for "Do you want to deploy your application"
    ```

    ![Worker Initialization](https://img.notionusercontent.com/s3/prod-files-secure%2Fc3841a92-a773-4ae2-b373-52b87f954981%2Fc5422c46-b2e2-4528-8319-7d8101498367%2Fimage.png/size/w=2000?exp=1737298294&sig=d87BkZ2O3opjEIQhIA3U4z6kSGkO6OwkPMF6hFPZvwQ)

2. **Start the worker locally**

    ```bash
    npm run dev
    ```

3. **Basic Server Code**

    Write your own code, or use the example below:

    ```javascript
    import { Hono } from 'hono';

    const app = new Hono();

    app.get('/', (c) => {
      return c.text('Hello from serverless backend!');
    });

    export default app;
    ```

Alternatively, clone this repository: [https://github.com/notcodesid/serverless-backend](https://github.com/notcodesid/serverless-backend).

## Deploy Your Server

1. **Login to Cloudflare via Wrangler CLI**

    ```bash
    npx wrangler login
    ```

2. **Deploy Your Application**

    ```bash
    npm run deploy
    ```

That’s it! Your application is now deployed.

💡 **For detailed notes, check Harkirat's notes**: [https://projects.100xdevs.com/tracks/eooSv7lnuwBO6wl9YA5w/serverless-1](https://projects.100xdevs.com/tracks/eooSv7lnuwBO6wl9YA5w/serverless-1)
