Model of Organization – To Be



# Summary of changes

Here describe at high level the change(s), and their motivation. Link with critical points identified in As Is analysis

The following sections are meant to describe in more detail the changes, using the same structure used in the As Is document.

# Organizational variables

Keep this section and subsections, if there is no change just write &#39;no change&#39;.  In case there is a change detail it.

## Size

## Products services

## Goal, goal type, vision, mission, strategy

## Culture

## Structure

### IT office

The IT Office will slightly change because new backend functionality will be added to manage the new application. The main change will be an reorganization of the existing team, creating a department entirely focused on the customer application.

## Formalization specialization centralization

## Organizational type

&#39;no change&#39;

# Business model canvas

![BMC](Images/bmc_tobe.png)

# IS Views

## Functional view, data

![UML class diagram](Images/data_model_to_be.png)


The new process is managed by an application that allows the automatization of the order request and the check of the state by the customer. For these reasons an account is required for both user and employee as even the workers will access the order information via the app.

Furthermore, it's now possible for the customers to add comments while approving or rejecting the proof and a design feasibility will be attached to each request, even when the request is rejected by the "Altopascio competence center".

## Functional view, processes

Write no change if the model remains as in As Is

### Process selection

Report the PICK chart (see process redesign chapter)  used to select the process to be changed and argument about it

### Process 1

The main problem we found in the As-Is product design process was the number of steps required to fufill a simple request to the Graphic's department. The End customer had to first contact the Essity Customer Service, then the CS had to contact the Altopascio competence center's Product service department, who would have to record in a database the requests to keep track of them. At this point the PS department could contact the Graphic's department and ask for the check and the proof realization. 
All these communications were done by email, so the process was bound to create difficulties in case of an human error (employee fails to send email) and it could take a great amount of time, especially if we consider that a product design can be sent back many times before the final approval. 

We can fix these problems using a specific application that gives direct contact between the End Customer and the Graphic's department. When the EC finished the product design example, he can upload it to the application using a specific request form and notify the Graphic's department, who can at that point start the procedure to check the feasibility of the design. All the communications and the feedback between the two entities can be done through the application, who will send a specific notification every time, and are stored in the application's database.

Every End Customer and Graphic's department employee has an account on the application, with specific privileges depending on their role in the process. The End Customer can check the state of the procedure in the application by logging into the page dedicated to the specific process.
The Essity Customer Service department's employees also have accounts to manage eventual assistance requests from the End Customers. 


![Proc1](Images/proc1_tobe.png)


| Activity in BPMN | Supporting Software functions |
| --- | --- |
|Create End Customer's account|POST EC's data|
|Upload new product design example|POST product design example|
|Add feedback to product design example|PUT feedback of design|
|Send request for proof realization| Create and Send notification|
|Create product design approval process|Create procedure in software application|
|Upload proof realization of design|POST proof realization|
|Add feedback to proof realization|PUT feedback of proof|
|Search for proof realization by design id| GET proof realization|
|Search for design example|GET product design example|
|Send approval for design feasibility| Create and Send notification|
|Send approval for  proof realization| Create and Send notification|



### Process 2

In the As-Is process the Planning Department has to check the raw material stock for every order received. If the materials are not enough to fufill the order, the department has to get in touch directly with the suppliers and reject the order while it waits for the Production facility to replenish their stock. This is a problem because it loses the company a lot of time waiting for the raw materials and it makes them postpone orders. 
To fix this problem we thought the Production Facility could implement its own checking process for the stock. 
Every material in the facility gets scanned manually with a bar code scanner and is recorded on the application so that we can keep track of the materials that exit the warehouse. The stock is checked by a production department employee through the application every day, and if it gets under a certain threshold the application manages the order request for the suppliers. After the supplier notifies the shipping of the raw materials, the production facility stock gets replenished. 
The application has an inventory of the products for the warehouse that are associated with a specific barcode. It also has an account for the suppliers and the production facility to manage the communications between them, for example when the production facility needs to order new material. 
In the application it's also possible to modify the stock's threshold.

![Proc2](Images/proc2_tobe.png)

| Activity in BPMN | Supporting Software functions |
| --- | --- |
| Scan new raw material | Barcode scanner |
| Add new material to inventory | POST material description and barcode  |
| Check if stock's is under threshold  | GET warehouse information and execute script based on BR|
| Modify stock's threshold | PUT new threshold |
| Create new production facility account| POST production facility data|
|Add new supplier to supplier list|PUT supplier's description|
|Make order to supplier|Create and send notification|

## IT view

### Application portfolio

Write no change if the portfolio remains as in As Is

Otherwise list here the new portfolio, highlighting new applications, and abandoned applications

#### Selection

Describe the applications considered for the selection

| Application name | Vendor | Description | Price model and fees |
| --- | --- | --- | --- |
|   |   |   |   |

Describe here how the selection of the new application was made

| Criterion | Application1 | Application2 | Application x |
| --- | --- | --- | --- |
|   |   |   |   |

Alternatively argue that the new application should be developed custom for the company.

#### Coverage

Show how the selected application provides the software functions needed (as identified in Functional view, processes section), discuss gaps, if any

| Software function needed (from process view) | Software function provided by application selected | Gap analysis |
| --- | --- | --- |
|   |   |   |



### Technological view
![DeploymentDiagramTOBE](Images/DeploymentDiagramTOBE.jpg)

The new Deployment Diagram highlights the introduction of the new applications.
The first one that manage the customer relationship from the assistance to the creation of a new order with a dedicated interface for draft approval. 
The second one concerns the orders for raw materials with the introduction of bar code scanner and the related bar code for the products.

#### Integration

In case a new application is introduced discuss how integration happens in terms of

Data exchange (which data is exchanged)

Control mechanism (mechanism used by applications to interact, ex message passing, rpc, etc)

# IT strategy

The introduction of a new application follows the Business Strategy of creating values, in this case, for the customer. II will likely need a reorganization in order to meet new requests on data management.

# Effect of change(s)

## Effect on KPIs and CSFs

(remark, KPIs and CSFs should not depend on the change, but should remain the ones defined in the As Is section – the goal being to compare the effect of the change on the same indicators)

Report only indicators that are supposed to change, argument on why the change has an effect on them, report how much the indicator could change. Do not forget the unit cost of the product / service.

| Indicator (Csf, Kpi) name | Effect | Quantitative estimate of variation (absolute, %) |
| --- | --- | --- |
|  CSF1: Customer Satsifation |  Increase because the customers have more managment and user-friendly with the app  |   +20% |
|CSF3|The customer service manage the comunication with the customer in a better way with a GUI and trough the app |+30%|
|CSF3.1|The response time (to process a new request from a EC and give to it a feedback) decrease thanks to the good realization of the all infrastructure around the new managment software |- 20%|
|CSF5|The number of merged order can be increase thanks to an algorithm| +15% |
|CSF9: Time from check stock of raw materials to order new materials or confirm planned SAP order|The process time has an important decrease because the app automatically manage if a new order is needed  |- 40%|


## TCO, ROI and Break even

Define the TCO for the change (use a 3 -5 years horizon)

Estimate costs (from TCO) and savings, and discuss the number of years needed to recover the investment

## Risks

Discuss the main risks (technological, organizational, human factors) related to the change, and what can be done to reduce them

# Conclusion

In summary, why the organization should buy (and pay for) your proposal of change?
