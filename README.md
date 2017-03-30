# Music-Store-
The websites of Music Store is designed for selling digital album
Actually It's my graduation design 
I want to make it perect ,also through this , I believe I can improve a lot


<h3>WebSites Design</h3>
<h4>In this websites I will make following functions</h4>
<ol>
  <li>Login/Register</li>
  <li>Shopping cart(CRUD)</li>
  <li>Order(CRUD)</li>
  <li>Review</li>
  <li>Collection</li>
  <li>Online help</li>
  <li>Online Payment</li>
  <li>Personal Managerment pages
    <ul>
      <li>Check Order</li>
      <li>Check Cart</li>
      <li>Modify Personal Information</li>
      <li>Add bank-card</li>
    </ul>
  </li>
  <li>
  <p>Admin</p>
    <ol>
    <li>Manage order(the status of order)</li>
    <li>Manege User(Check)</li>
    <li>Manege Review(Delete)</li>
    <li>checking admin</li>
    <li>commodity's CRUD</li>
    </ol>
  </li>
</ol>
<h4>The following are the websites design</h4>
<ol>
  <li>
  Index.html
  <ul>
    <li>It will look like Apple's Home Page</li>
    <li>The Search will be changed(actually use modal)</li>
    <li>Add more 'div' to show the Information</li>
  </ul>
  </li>
  <li>
  Details.html
    <ol>
      <li>I'll use this page to show more detail's of album/artists</li>
     <li>meanwhile you can filter the informaton of artists and albums</li>
    </ol>
  </li>
<li>
Carts.html
  <ol>
    <li>It's the page about shopping cart</li>
    <li>In this page you can check your carts and delete the commodity,add the number of commodity </li>
  </ol>
</li>
Order.html
<ul>
  <li>User can check their order</li>
  <li>the total number of the cost</li>
  <li>insert or modify the details of order(not include the commodity's content)</li>
</ul>
  Pay.html
  <ul>
    <li>the page is made for user to pay their money</li>
  </ul>
<ol>
<p>-----------------I'm the divided line---------------------------------</p>
<h3>After finish the web pages that show for user,I'll design the database table</h3>
<ul>
  <li>
    <p>the user table(tb_user)</p>
    <ol>
      <li>ID</li>
      <li>Username</li>
      <li>password</li>
      <li>email</li>
      <li>phone</li>
      <li>createdate</li>
    </ol>
  </li>
  <li>
    the userDetails tabl(tb_userDetails)
    <ol>
      <li>ID</li>
      <li>userID(foreign key reference tb_user ID)</li>
      <li>gender</li>
      <li>birthday</li>
      <li>location</li>
      <li>profile</li>
      <li>nickname</li>
    </ol>
  </li>
  <li>
    tb_album
    <ul>
       <li>albumId</li>
       <li>albumName</li>
       <li>genre</li>
       <li>loaction</li>
       <li>releaseDate</li>
       <li>imgUrl</li>
       <li>addDate</li>
       <li>company</li>
       <li>status</li>
       <li>leftnumber</li>
       <li>description</li>
       <li>genreId</li>
       <li>artistId</li>
    </ul>
  </li>
   <li>
    <ul>
    tb_genre
       <li>genreid</li>
       <li>name</li>
    </ul>
   </li>
    <li>
    tb_artist
      <ol>
         <li>artistId</li>
         <li>name</li>
         <li>description</li>
         <li>localId</li>
      </ol>
    </li>
    <li>
    tb_local
      <ol>
        <li>localId</li>
        <li>name</li>
      </ol>
    </li>
    <li>
      <ol>
      tb_song(evey album contains songs )
         <li>songID</li>
         <li>albumId</li>
         <li>name</li>
      </ol>
    </li>
    <li>
     <ol>
     tb_advice(every user have their advise)
       <li>adviceId</li>
       <li>userId</li>
       <li>content</li>
       <li>createdate</li>
    </ol>
    </li>
  <li>
  tb_cart
    <ol>
      <li>cartId</li>
      <li>userId</li>
    </ol>
  </li>
   <li>
   tb_cartDetails
    <ol>
     <li>cartDetails</li>
     <li>cartId</li>
     <li>albumId</li>
     <li>quantity</li>
    </ol>
    </li>
    <li>
    tb_collection
      <ol>
       <li>collectid</li>
       <li>albumid</li>
       <li>userid</li>
      </ol>
    </li>
   </li>
   <li>
    <ol>
    tb_order
      <li>orderId</li>
      <li>orderdate(the day you pay)</li>
      <li>createDate(the day order created)</li>
      <li>total</li>
    </ol>
   </li>
   <ul>
   tb_userDetails
    <li>orderDetailsId</li>
    <li>orderId</li>
    <li>albumId</li>
    <li>quantity</li>
    <li>unitprice</li>
   </ul>
   <li>
   </li>
</ul>
----------------above are the tables I need to create----------

-----The main tech I'll use is .NET MVC ------------
<h3>Today is March 30</h3>
<p style="color:green">Don't cry because it's over, smile because it happened.</p>

The following are the Schedule I have made

2 weeks edit the webpage
1 week create the table and insert the sample data 
2 weeks add the function 
1 week write the graduation report 
then....
preparing for gradute 
<p style="color:grey">(Actually I really look forward for a graduation travel with my best friend 
but...
There maybe have so many uncertain parameters
Anyway I'll try.)</p>
Problems and difficulties in life are common but it's the attitude that makes the difference.

+++++++++write down the problems I have met+++++++++++++
//Add new data to database    Star:*
 Solution :
  there lots of ways to solve it 
 Here is way I use:
  use From request
   Forexample:
       [HttpPost]
        public ActionResult Test(string id)
        {
            //id is the value from View 
            //every from need a Name,method, action
            return View();
        }
        
  //Query data and input in View Star:**
  I'm not good at LINQ so I use database Procedure to resolve 
  Example:
   public ActionResult Artist(int id) {
            var artistInfo = new ArtistDetails();
            //LINQ for artist
            artistInfo.artistSingle = (from at in musicDB.tb_artist
                                 where at.artistId == id
                                 select at).Single();
            //lamda expression of query album
            artistInfo.albumModel = (from al in musicDB.tb_album
                                     where al.artistId==id
                                     select al
                                         ).ToList();

           //the procedure for artist
            SqlParameter atId = new SqlParameter("@artistId",id);
            artistInfo.artistModel = (musicDB.Database.SqlQuery<tb_artist>(
                "exec artistProc @artistId",atId
                )).ToList();
            return View(artistInfo);
        }
        
   
  

