- {{renderer :wordcount_}}
	- Content management systems ( CMS ) are a type of software that allows users to create, manage, and modify content on a website without the need for specialized technical knowledge.
	- Early CMS software was designed to simplify the process of creating and managing websites, and was primarily used by web developers and were often incorporated into the web platforms themselves. WordPress, for example, is a framework for creating web sites and web content but is also a CMS that can be used to create and manage content.
	- I worked with web programmers that started out on HTML, CSS as it became available and then PHP, MySQL, and JavaScript as the ecosystem around building web sites came to be. Some would have written their own CMS, others would have used a CMS that was available at the time but ofcourse, there would have been a time when there was no CMS that was widely available, let alone open source ones. Indeed, to this day, there are many commercial solutions that provide for contnet management and which in some cases, eye wateringly expensive and used by companies perhaps as a status symbol.
	- An intersting comment I remember from one such developer who had written their own CMS and from time to time continued to do so was that with solutions such as Drupal and Wordpress, that he said that he regretted having done so as this was such a time consuming task and that he would have been better off using one of the open source solutions that were available at the time. But that said, I would suggest that the very process of writing a CMS would have been a great learning experience and would have given him a deep understanding of the problem domain. Indeed, I as a developer worked on monitoring and availability software that were arguably available as commercial softwares but which were extremely expensive at the time, so writing our own bespoke soluiton that became successeful and cost effective but later could well have been replaced by open source solutions such as Nagios and Zabbix was not a bad thing, as it gave us something that was needed at the time. So in the case of things like CMS software, wrting your own might have been not so much of a bad thing, if only character building. However now, with a plethora of open source alternavies for CMS and all sorts of things in other domains, it makes sense to use these rather than reinvent the wheel. For learning, it is usefull to create a simple, cut down version for a project but for production, it is best to use something that is tried and tested and which has a community around it. If your still hungering and thirsting to do more, becoming part of a community that develops an existing solution could be a good way to go. But I would reason in my own mind that starting an entirely new 'thing' needs careful consideration and a good reason for doing so.
	- As it was almost the accepted way that any web framework, often written in PHP, would have had a CMS in built, it was not uncommon to think of CMS as being the web framework itslef. However over the last 10 years or so, this boundary has gradually changed to the point where we now have the term 'headless CMS' where by the contntent management system is entirely separate to the web site technology all together. The two disciplines are thus parted, CMS being a domain of its own. Interoperability between the two is evolved to a number of different integrations, most of which follow a RESTful API approach. Some have also adopted GraphQL as a means of integration. The advantage of this approach is that the CMS can be used to manage content for a number of different web sites and web applications, and indeed, other applications such as mobile apps. The CMS is thus a central repository for content that can be used by a number of different applications. This is a powerful concept and one that is becoming more and more popular.
	- There are open source CMS solutions that can be self hosted and perhaps many more that are offered as web services that are often paid for on some kind of subscription basis. This software as a service approach is popular with companies and organisations that do not want to become involved in the technical aspects of hosting and maintaining the CMS software. The advantage of this approach is that the CMS is maintained by the service provider and the user can concentrate on the content and the web site or application that is consuming the content. The disadvantage is that the user can become tied to the service provider and if the service provider goes out of business or changes the terms of the service, the user is at the mercy of the service provider. Some call this 'tie in' or 'vendor lock in' and others I have come across may go to somewhat extreme measures in order to avoid said lock ins. Perhaps some may go too far and with the risk of re-inventing wheels but that is a topic perhaps for another time.
	- The CMS that I have chosen to look at for some projects I am working upon is Sanity.io.
	- I chose this CMS for a number of reasons.
	- Sanity gives its users access to what they like to call a 'content lake'. This is a central repository for content that can be used by a number of different web sites and applications. Put simply, each account holder in Sanity has a bucket in which they can deposit any or all of their content in a way that can be programmatically acceessed by any number of web sites and applications.
	- some aspects of Sanity are open source, for example, the 'studio' that is the softare that is used to add and edit content is based upon React and is open source, so when getting started with Sanity, you can run a command line tool that will create an empty or partly populated project that is a React application that can be run locally and which can be used to add and edit content. When your happy with any customisations you may need to make in this React application, you can deploy it to Sanity's servers and it will be available to you and your team to use. Alternatively, as it is a react project, you can host it yourself and make any further customisations you need to make.
	- In the mean time, your content is stored in Sanity's servers and is available to you and your team to use.
	- So this gives us a number of possibilities and options pretty much 'for free' and 'out of the box', so long as you already are happy to use React. As a react users and developer I found this to be a good fit for me and my team.
	- Sanity has its own query language that they call [groq](https://www.sanity.io/docs/groq) and which I like due to its simlicity and pragmatism. It is a query language that is easy to learn and understand and which is powerful enough to do most things that you would want to do with a CMS. It is also a query language that is easy to integrate into a React application. Also, sanity can use [Graphql](https://www.sanity.io/docs/graphql) to query your content. So if you dont like Groq for whatever reaason, GraphQL is also available for the cool kids that want to use it.
	- The editor is relatively staight forward to customise, once you get your head around its configuration driven approach. It can be extended to use React components, so you can add your own custom components as plugins. With this kind of extensibility, the sky could be the limit in terms of what you can do with the editor.
	- Out of the box, the Sanity editor is simple and intuitive to use. It is a WYSIWYG editor that most non technical users can become productive with in a short space of time. I would have to say that in comparison to things like Wordpress, Sanity studio is far simpler and less daunting to use, particularly if your not that technical.
	- Cost has to be a consideration, even if you or your company have the atituded that 'if you need to ask, you can't afford it', as no matter who or what you are, everything has a cost and making the best financial and purchasing decisions is the most efficient thing to do, in a world that is finite. We have to be aware that constantly consuming ever more and more resources is not suststainable.
	- Sanity const model is flexible and goes from nothing, in their free tier, to enterprise and scales on a per user basis with the free tier permitting upwards of 3 admin users, I believe they are changing this to 20 users to paid tiers at $15 per user on a monthly basis. With a sinlgle collection of data and I think 2 projects per account, this allows for small companies and start ups to get going with Sanity and to scale up as they grow.
	- The Sanity free tier claims to be [free forever](https://www.sanity.io/pricing) so if your botherd that you may be tied in to something that is initially free to then be charged ever increasing amounts, you can be assured that Sanity will not do this, at least for the free tier and possibly for as long as they are saying this. There is a commitment to keeping the free tier free and this is a good thing, at least for now. We've all seen free tiers made not free, cough Heroku, being one example but we have to be realistic and understand that nothing is free and that we have to pay for things in some way or another. Sanity is a business and they have to make money to survive and to grow. It is logical and reasonable to expect that if using a service like that when money is being made by its users, that they should be responsible to pay for the services they consume in order for that service to be sustainable.
- {{renderer :wordcount_}}
	- can you back it up ? https://snapshooter.com/application/sanity
		- this is a commercial solution, so is worth a look as it must have some kind of SLA
		- there is a free option for 1 dataset, 1 day, 1 automation, so for a non profit / charity this also is an option
	- what other backup options are there ?
		- at https://www.sanity.io/docs/export :
		  ```bash
		  curl https://<projectId>.api.sanity.io/v2021-06-07/data/export/<dataset>/ > backup.ndjson
		  
		  curl https://<projectId>.api.sanity.io/v2021-06-07/data/export/<dataset>?types=author,book > backup.ndjson
		  ```
		  so a command line, single command of some kind can be automated
		- at https://www.sanity.io/docs/importing-data :
			- ```bash
			  sanity dataset import my-data-dump.ndjson production
			  ```
	- image export in the backup command does not happen, so this is entirely misleading
	- there seems no clear path to export (both) images and documents to then restore (both) post to site loss or damage
	- this is wholly unnaceptible
	- https://www.sanity.io/help/import-asset-file-does-not-exist
	- this is useless, where a backup has an image embedded within it and a datastore is deleted or the backup is from another datastore, the image is present in the backup file but because the path does not yet exist in the datastor target, it will not restore from the dump, rendering the backups useless
	- I could have a way out of this mess
		- the data is stored in the backup file as base64, so could be editted out, the base64 string de-encoded to be a stand alone file, the base64 string be replaced with something like
		  `image@file:///local/path/to/rogue-one-poster.jpg` from `"data:image/jpeg;base64,/9j/2wB...` and maybe, just maybe, this could work, but only testing will prove this
		- its still very, very poor
	- can you get data out, regardless of platform, just show me the code
		- ```javascript
		  // Import the Sanity client library
		  import { createClient } from '@sanity/client'
		  import imageUrlBuilder from '@sanity/image-url'
		  import {toHTML} from '@portabletext/to-html'
		  import dotenv from 'dotenv'
		  dotenv.config()
		  
		  export const client = createClient({
		      projectId: process.env.PROJECT_ID,
		      dataset: process.env.DATASET,
		      useCdn: true, // set to `false` to bypass the edge cache
		      apiVersion: '2023-05-03', // use current date (YYYY-MM-DD) to target the latest API version
		      // token: process.env.SANITY_SECRET_TOKEN // Only if you want to update content with the client
		  })
		  
		  
		  const builder = imageUrlBuilder(client)
		  
		  function urlFor(source) {
		      return builder.image(source)
		  }
		  
		  
		  // uses GROQ to query content: https://www.sanity.io/docs/groq
		  export async function getPosts() {
		      const posts = await client.fetch('*[_type == "post"]')
		      return posts
		  }
		  
		  // create an array to store posts
		  const postArray = []
		  
		  // get all posts
		  export async function getAllPosts() {
		      const posts = await client.fetch('*[_type == "post"]')
		      // loop through posts and add to array
		      posts.forEach(post => {
		          postArray.push(post)
		      })
		      return postArray
		  }
		  
		  // get all post slugs
		  export async function getAllPostSlugs() {
		      const posts = await client.fetch('*[_type == "post"]{slug}')
		      return posts
		  }
		  
		  // get post by slug
		  export async function getPostBySlug(slug) {
		      const post = await client.fetch(`*[_type == "post" && slug.current == "${slug}"]`)
		      return post
		  }
		  
		  
		  
		  getAllPosts().then(posts => {
		      posts.forEach(post => {
		          console.log(post.title)
		          console.log(post.slug.current)
		          console.log('post body html : \n',    toHTML(post.body, {
		              components: {
		                /* optional object of custom components to use */
		              },
		            }))
		  
		  
		          console.log(post._updatedAt)
		          console.log(post._createdAt)
		          console.log(urlFor(post.mainImage.asset._ref).width(1200).url())
		      })
		  }).catch(error => {
		      console.log(error)
		  })
		  ```
	- backup and DR conclusions so far
		- it seems that so long as you dont _ever_ delete a dataset, you can restore from a backup file in sanity. 
		- howeer, as soon as the dataset that was originally backed up is deleted, the backup file is useless
		- the backup file is in ndjson format, so can be edited, so there is a possibility that in line base64 data could be extracted, the file re-written to use local files paths and then re-imported, having created the local files and paths using the base64 data
		- by manually editting a backup file, I found that this was only partially successful. Each file I replaced that was in line resulted in an image that appeared inconsistent with that of the image that was visible when the database was intact and the post was being viewed normally. As each file was replaced with that of a png, a further one needed to be replaced. that occured further on in the file and there were additional files that were webp format, which I did not get as far as trying to replace. So this would need to be revisited and a more robust solution built around the idea of parsing the ndjson file and extracting the base64 data, creating the files and paths and then re-importing the data. This would require work and would need to be tested thoroughly. It would also need to be automated, so that it could be run as a cron job or similar. 
		- so long as the web site that is subsequeently created from a sanity cms, as with any other cms, back-end system, database or whatever is kept separate from the pipline that creates it from, in this case, the sanity database, then the web site itself could be backed up, archived and version controlled such that in the case of a disaster recovery, this  well known and structured website comprising of image assets, json data and markdown files could be used as a single source of truth to recreate the web site. 
		- Other cms solutions could suffer from the same or similar issues. Whilst sanity is partly open source, in that its front end, management software and text editor, also the standard that it uses by which to store data, are open source, the back-end 'data lake' and its own inner workings are not. So the issue with images being stored in the backup file but clearly the data lake holds these separate to that of the text data, this is just how it works and that fact that the export / import process does not out of the box to cater for this is something that needs to be decided on by the user as to whether they are happy with this or not.
		- for the moment, these disadvantages I believe are outweighed by the benefits of the free tier enabling 0 start up costs for SMEs and startups, including not for profit and charitable organisations
		- The work around of archiving a complete, working and completely formed static site, using any static site generator, be it Astro, Gatsby, Next, Hugo, Eleventy or whatever is a possible resution to an annoying problem
		- A re-engineering of the export / import process to separate image assets from textual data is a possibility and one that I could explore and ask about in the development community. Slack seems to be the way that Sanity developers communicate with each other, so I could ask about this in their #help channels before tring to fix the problem myself and when there could be a known solution that I am not aware of as to yet.