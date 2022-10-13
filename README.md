# Group Reveal

## Motivation

The intent of this project is to allow reveal of sensitive information, but 
only if a sufficient group assembled.  For example, one may want to transfer
important and sensitive information like "death docs" or financial info,
but only in the event that they actually pass away.  This project is to 
explore possible solutions to this problem.

## Requirements

1. No personal data released to 3rd party services
2. Service components are self hosted and self controlled
3. Personal data for reveal can be arbitrary
4. Revelation of personal data through trusted parties, but only
   if sufficient quorum of trusted contacts assemble.
5. Originator of group reveal data can revoke access or change
   stored data at any time so that it can no longer be revealed
   by quorum.

## Approch

The the core sensitive data is assumed to be stored within an encryped volume
created by the user on their own computer. Such a volume can contain 
arbitrary files a user may wan to share such as "death docs" with detailed
info on insurance and financial accounts.  Veracrypt provides existing 
capabilities for such volumes, though there are certainly other options.

The volume itself is not provided to the group as doing so would prevent
the originator from changing the stored data or revoking data from the 
quorum.  Instead the encrypted volume is stored in an alternate location
and the location as revealed as part of the group reveal process.  The 
volume can be removed to revoke access, or be updated in place to allow
changes. 

Notionally the volume can be stored on a public file server (ideally self
hosted) in order to allow the quorum to access the contents when revealed. 
Alternatively the file can be stored on some drive the quorum is able to access
at the appropriate time.

Given the sensitive nature of the file contents, no single member of the group
should be able to reveal the secret and retrieve the data. For redundancy it 
is also desirable to have to flexibility in those that are able to form quorum.
For example allowing data to be revealed if any 3 out of 5 group members find
it appropriate to reach quorum. An algorithm called 
[Samir's Secret Sharing](https://en.wikipedia.org/wiki/Shamir%27s_Secret_Sharing) 
(or SSS) provides a way for splitting a secret such that the secret is 
revealed only if sufficient secret shares are assembled. Using this algorithm 
we can generate a number of shares appropriate for the larger group and also 
constrain to have any subset of those shares to reach quorum. 

In this usage the message secured by SSS can be the pointer to the 
original encrypted volume as well as the decryption password required to
view the volume.

The SSS shares are generated using a local and self-hosted version of the 
algorithm to prevent inadvertent sharing with 3rd party services.  The shares
are all present at creation, but special care should be taken when 
distributing shares to group members.  Group members should be provided not
only their share token (text string) but also instructions regarding when 
shares should be assembled, and how the shares should be assembled with 
others in the group.

The reassembling of shares for group reveal is also performed with a self-hosted
version of the algorithm to prevent inadvertent sharing with 3rd party services.
Once the password and path the encryped volume are revealed, the volume can be
opened and the data group data is revealed.

## Alternate Solutions

There are some options from existing services (like google or facebook) to
have certain information revealed after a user has not logged in and the
service becomes inactive.  Unfortunately, these services have some drawbacks:
  - inactivity time periods are necessarily large to prevent falsely
    sending info
  - require accounts and usage of external services
  - limited flexibility on what is revealed

This alternative list is certainly not exhaustive and can be updated from time
to time.  Other solutions may be more appropriate for your uses.