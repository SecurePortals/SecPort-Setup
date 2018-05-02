# Integrity Checks

> Conecpt: We gotta make sure our data is secure, and rules are being followed. If our data is corrupt, we gotta know asap. The following are four seperate projects, all of which test the Integrity and Reliability of our data. 

## Orphan Records

> For this project, we're going to look for Orphan Records. Here's a scenario: A user creates a log in, goes through the whole process of inputing tenant information in, and then proceeds to the web app. The first time they get all the way through, but for some reason after everytime they log off, they have to re-enter all of their tenant information to log in. The problem here could be that our database is not properly associating the USR_ID in LOGIN with a USR_ID in TENANT. These would be considered Orphan Records. There should be a valid USR_ID in the TENTANT/LOGIN relationship. 

> The script will be called 'data_intg_orphans.py', and will address the following questions:
1. Is there a matching USR_ID for every record in TENANT/LOGIN? ADMIN/LOGIN? OWNER/LOGIN? MANAGER/LOGIN?
2. Does every PROPERTY have a valid OWNER_ID?
3. Does every UNIT have a valid PROPERTY_ID?
4. Does every TENANT have a valid LEASE_ID?
5. More...

## Business Rules

## Database Clean Up

## Database Security
