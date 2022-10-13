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

TBD

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