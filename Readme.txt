**PROJECT OVERVIEW**



**Project Name:** AI-Powered Property Recommendation via Contact Request \& CRM\*\*



**Overview**



This project builds an AI-driven recommendation system that responds to user property requests submitted through the \*\*Contact Us\*\* form on a real estate website.



When a user submits a request specifying budget, location, property type, and preferences, the request is:



1\. Stored in the **CRM** as a lead

2\. Processed by the backend

3\. Passed into a vector search engine

4\. Used to retrieve the most relevant property listings

5\. Returned to the user via the **website chat interface** as recommended property links



This system improves lead response speed, relevance, and conversion by providing instant, intelligent property suggestions



**MVP(Minimal Viable Product) DEFINITION**



**MVP Goal**



Deliver **instant property recommendations** based on user specifications from the Contact Us form, while logging the request in the CRM



**MVP Scope (Phase 1)**



User Flow



1\. User clicks **Contact Us**

2\. User submits:



&nbsp;  \* property type

&nbsp;  \* location preference

&nbsp;  \* budget

&nbsp;  \* specifications



3\. Request is:

&nbsp;  saved in CRM

&nbsp;  sent to recommendation engine



4\. User receives:

&nbsp;  5–10 recommended property links in chat



&nbsp;**Components**

* Contact Us form
* Backend API to receive lead
* CRM lead ingestion
* Vector search–based recommendation engine
* Chat response with property cards or links



**Recommendation Logic (MVP)**

* **Hard filters:** budget, listing type, location
* **Vector similarity:** semantic matching of property descriptions
* **Re-ranking:** closeness to budget + preference match





**Out of Scope (For MVP)**

* Personalized long-term user profiles
* Payment or booking
* Mobile app
* Analytics dashboard
* Agent assignment logic





**MVP Success Criteria**

* Recommendation response time < 2 seconds
* At least 70% relevance in manual review
* Works with ≥ 1,000 property listings
* CRM successfully stores every request





**ROLE ASSIGNMENT (TEAM OF 4–5)**



**AI / ML Lead**

Responsibilities:

* Define recommendation strategy
* Design embedding \& vector search pipeline
* Build Colab notebooks
* Define input/output schemas
* Validate recommendation quality



Ownership:



* Vector index
* Query logic
* Recommendation relevance



**Backend Engineer**

Responsibilities:

* Contact Us API endpoint
* CRM ingestion
* Recommendation service orchestration
* Chat response handling



Ownership:



* API contracts
* Service reliability



**Frontend Engineer**

Responsibilities:

* Contact Us form UI
* Chat interface UI
* Rendering recommendation cards/links



Ownership:



* User experience
* API integration





**Data / Infra Engineer (Optional but valuable)**



Responsibilities:



* Property dataset preparation
* Data cleaning \& normalization
* Storage \& deployment setup



Ownership:



* Data quality
* Environment stability





**Leadership rule:**

You own decision clarity, not all the code.





**DATASET PREPARATION (YOUR FIRST TECH TASK)**



**Required Property Dataset Fields**

Each property listing **must** include:



| Field         | Description                    |

| ------------- | ------------------------------ |

| property\_id   | Unique identifier              |

| title         | Short property title           |

| description   | Full description               |

| listing\_type  | sale / rent / shortlet         |

| property\_type | apartment / duplex / land      |

| price         | Numeric value                  |

| location      | City / area                    |

| bedrooms      | Integer                        |

| bathrooms     | Integer                        |

| amenities     | List (parking, security, etc.) |

| url           | Public listing link            |

| status        | available / unavailable        |





**Fields Used for Vector Embeddings**



These fields are **combined into one semantic text**:



* title
* description
* amenities
* location
* property\_type
* listing\_type



Example combined text:



> “3 bedroom furnished apartment in Lekki Phase 1 with parking, 24-hour security, close to the beach.”





Fields Used for Filtering (NOT embeddings)



* price
* listing\_type
* location
* bedrooms (if strict)



**Dataset Sources**

* Existing company database
* Export from CMS
* Scraped listings (if approved)
* Mock dataset (for early MVP)



**Output of Dataset Preparation**

* Cleaned property table
* Text field for embeddings
* Metadata table for filters
* Ready for FAISS indexing





**CRM INTEGRATION (MVP VIEW)**

CRM Receives:

* User contact info
* Property request specs
* Timestamp
* Recommendation IDs returned



Why this matters:

* Agents can see what was recommended
* Follow-up becomes context-aware
* Better conversion tracking



