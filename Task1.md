# Integration of a new payment gateway
Integration of a new payment gateway is an essential technical process for online stores to offer a variety of payment options to their customers. Payment providers can implement their integrations using the **Payment Provider Protocol**. This protocol allows providers to create a payment connector that interacts with our Gateway. After developing the connector, providers also need to test it and ensure that they follow the necessary security standards before it can be available to stores, for this reason some steps need to be followed to ensure the security of customer data and the correct system functioning.

There are some steps to follow:
* 1\. Payment Connector Check:
    * a\.  Make sure your payment connector supports credit cards.
    * b\. Make sure your payment connector supports debit cards.
    * c\. Make sure your payment connector supports co-branded cards.
    * d\. Make sure your payment connector is PCI-DSS compliant.
    * e\. Consider hosting the connector in a secure environment.
    * f\. Consider using a Secure Proxy that receives tokens instead of sensitive card data.
* 2\. Payment connector implementation:
    * a\. Follow Payment Provider Protocol.
    * b\. Implement all required endpoints.
    * c\. List all payment methods supported by the integration in the List Payment Provider Manifest endpoint response.
    * d\. Implement specific behavior for each payment method in the Create Payment endpoint.
* 3\. Payment connector test:
    * a\. Install the payment connector in a store.
    * b\. Test each endpoint using the Payment Provider Test Suite application during the homologation step.
* 4\. Approval:
    * a\. After passing the tests, open a ticket so that our team can carry out the approval process.


## Payment Provider Protocol

The VTEX Payment Provider Protocol is a set of standards that must be followed to implement payment integration in an online store. This protocol includes a series of endpoints that must be implemented, such as the creation of payment, refund and payment confirmation, in addition to the list of payment methods supported by the integration.

Before starting the implementation, it is important to ensure that the payment connector complies with the set of security standards for credit and debit card transactions. This can be done by hosting the connector in a secure environment or by using a Secure Proxy that receives tokens instead of sensitive card data.

After implementation, it is necessary to carry out the approval, which consists of testing each endpoint of the connector using the Payment Provider Test Suite application. When the connector passes all the tests, a ticket must be opened so that the homologation team can carry out the final approval process.

VTEX supports multiple payment gateway affiliations, allowing you to configure a set of settings that represent your contract with a payment gateway of choice. This allows different types of transactions to be processed by different payment gateways on the webshop.

## Payment Connector

The VTEX Payments module offers a variety of connectors, which are communication protocols necessary for the transmission of data between your store and the acquirers, sub-acquirers or gateways responsible for processing payments. To make a payment method available on your website, you need to activate the connector that communicates with the corresponding gateway.

An important characteristic of this module is that it allows a connector to establish communication with several means of payment, and vice versa. This requires configuring the connector through gateway affiliations, which are sets of settings that represent the contract with a chosen payment gateway. With this, it is possible to decide which payment gateway the different types of transactions in the VTEX store will be processed through.

## Payment Provider Implementation

The integration must follow the protocol defined by VTEX, which includes the implementation of endpoints to create payments, list payment methods, confirm payments and perform refunds.

Endpoints are implemented by the payment provider and must follow the VTEX protocol.

Key endpoints include:

- `GET /api/pvt/payment-methods`: lists the payment methods supported by the payment provider.
- `POST /api/pvt/order/:orderId/payment-notification`: sends a notification to VTEX informing about the payment status.
- `POST /api/pvt/orders/:orderId/payments`: creates a new payment for a specific order.
- `POST /api/pvt/orders/:orderId/payments/:paymentId/void`: cancels a payment.
- `POST /api/pvt/orders/:orderId/payments/:paymentId/refund`: makes a refund for a specific payment.

It is important that the payment provider test and certify the integration before making it available to end customers.

## Homologation

When finalizing the integration of your payment system, it is important to verify that it was carried out correctly. To do this, use the Payment Provider Test Suite to simulate the integration and test that everything is working as it should. This will ensure that your customers can make payments securely and efficiently.

Here's a step-by-step guide on how to download and install the Test Suite application:

1. Access VTEX Admin.
2. In the **Account Settings** module, select Apps and then App Store.
3. Search for **Payment Provider Test Suite** in the search bar.
4. Click **Install**.
5. You will be redirected to the VTEX App Store. Click the **Get App** button in the top right corner of the page.
6. Then, on the popup screen, enter your account name - in lowercase letters with no spaces between them - and click **Confirm.**
7. Click **Install** to complete the installation process.

After completing the approval process, run tests to validate the integration using the Test Suite application.

## Know more
- [Payment Provider Homologation](https://developers.vtex.com/docs/guides/payments-integration-payment-provider-homologation)
- [Configure a payments connector](https://help.vtex.com/pt/tracks/pagamentos--6GAS7ZzGAm7AGoEAwDbwJG/7pAEMAo4iqNHwYOarZ3zgm)
- [Payment Provider Protocol](https://developers.vtex.com/docs/guides/payments-integration-payment-provider-protocol)
- [Implementing a Payment Provider](https://developers.vtex.com/docs/guides/payments-integration-implementing-a-payment-provider)
