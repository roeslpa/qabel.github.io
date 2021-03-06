---
title: Local Data
---
# Locally stored Settings and Information

## Abstract
Information and configuration settings stored on each client.

## Local settings

The preferences are a collection of settings which describe some common settings
for the library, the UI and for the communication with the Qabel servers.

default: true

* poll_interval: default polling interval
* drop_last_update: time of last drop message request; time stamp of the received drop message is used

Summary

        preferences     = "{"
                        'poll_interval' : NUM,
                        'drop_last_update' : STR,
                        "}"

## Client Data

A device stores two types of settings and information regarding the user:

 * accounts
 * identities

Summary

        Settings        = "{"
                        'accounts' : accounts,
                        'identities' : identities
                        "}"

It also stores information on the users contacts.

### Accounts

Accounts are meant for paid service accounting. These credentials can be used to gain write access to S3.

The item `accounts` includes an array of account settings structures

Summary

        accounts        = "["
                        account*
                        "]"


### Account

        account         = "{"
                        'username': STR,
                        'email': STR,
                        'password': STR,
                        "}"


### Identities

The item `identities` includes an array of identity settings structures

Summary

        identities      = "["
                        identity*
                        "]"

### Identity

| Key | Description |
| --- | ----------- |
| alias | Textual, user-defined label identifying this identity (also to other users) |
| email | Email address of the user owning this identity (optional) |
| phone | Phone number of the user owning this identity (optional) |
| private_key | Private, secret part of the key pair |
| public_key | Public part of the key pair |
| dropUrls | List of [urls](../Qabel-Protocol-Drop#url) of the drops where the identity expects to receive messages |


Summary

        identity        = "{"
                        'alias' : NAME,
                        'email': STR,
                        'phone': STR,
                        'private_key' : KEY,
                        'prefixes': [STR],
                        'dropUrls' : [URL]
                        "}"

## Contact Data

Additionally to the data on the user itself information on its contacts can be stored on the device.

Summary

    Contacts        = "{"
                    'contacts' : contacts
                    "}"

### Contacts

The item "contacts" includes an array of "contact"s

Summary

    contacts        = "["
                    contact*
                    "]"

### Contact

The following items define a contact item:

| Key | Description |
| --- | ----------- |
| alias | Alias for the contact |
| email | Email address for the contact (optional) |
| phone | Phone number for the contact (optional) |
| public_key | Public key of the contact |
| dropUrls | Array of drop Urls |

Summary

    contact         = "{"
                    'id': INT,
                    'alias': NAME,
                    'email': STR,
                    'phone': STR,
                    'public_key' : KEY,
                    'dropUrls' : [STR],
                    "}"

### Example

```json
{
  "id": INT,
  "alias": "Alice",
  "email": "alice@example.org",
  "phone": "+49123456789012",
  "public_key" : "feffe9928665731c6d6a8f9467308308feffe9928665731c6d6a8f9467308308",
  "dropUrls" : ["example.org/jkl"],
}
```
