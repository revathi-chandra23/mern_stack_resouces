authentication / authorization

Authentication:

- it is a process of identifying who the user is

Authorization:

- it is process of determining what access does th user have

authentication - signup
{email, password} - hash the password - save in the database.

         Hashing vs Encryption


         pwd ---> qxe
            key= 2*nextablphabet +3
         momo--> npnp
         cab --->dbc


          mno <--  nop

          encription is reversible
                encrypt <----> decrypt.
                         key

        hashing is irreversible

        xyz ---> alogrithm ---> lksjldefkjasfjsij2slkjfoiij39
        abc ---> alogirthm ---> skjdfifjsodfjlj


        login
        abc ---> alogirthm (sha_1)---> skjdfifjsodfjlj

        a-->b
        b--->c
        d--->x
        x--->sdfv
        ab--->klsdflk
        bc--->sldfklj

Salt
adding extra to hash alogirthm

signup: mahesh --> hash algorithm + salt(3 salt round) ---> hsidjfisdofjsldfkj

login: mahesh --->hash algorithm + salt(3 salt round) ---> haslkjdflksjdlfkjlk

hash algorithm + salt + secret_key

- login:
  {email, password}
  compare with the hashed string
  ? login successful,generate and give back jwt  
   : wrong password/ invalid cred

get /report ---> {email , password}---> token

- if token is valid
  ? we give access to the data;
  : login first

  express application-->
  authentication ----> /register, login
  /---> doesn't require authentication
  /notes ---> require authentication

  blacklisting

  get authentication, /logout
  blacklist that token ---> maintain a blacklist where you add this token.

  GET authenticate, /notes
  first check if \_token\_\_ iis present in blacklist
  ? login again
  : jwt.verify()
  ? / notes
  : /login again

  ***

  refresh tokens:

client---signup---->server

client ---login --->server

client<-----jwt(7day )---server

client--/notes----> server

after token expired the client need not login again and can use refresh token to get a new normal token.

1. when someone logins , apart from normal token, we also give them refresh token
   /login
   normal token-->7days. /30min /5min
   refresh token--->28day /1day /30min

   after 7days

   /notes
   normal token --->expired

   refresh token---> we will create a new token

   /refresh
   verify(refresh_token) ? new normal token(7day validity) : plz login again
