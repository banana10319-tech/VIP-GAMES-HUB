*{
  box-sizing:border-box;
  margin:0;
  padding:0;
}

body{
  font-family:Arial,sans-serif;
  background:#070b10;
  color:#fff;
  min-height:100vh;
}

/* Header */
header{
  position:sticky;
  top:0;
  z-index:10;
  height:58px;
  padding:10px 14px;
  background:rgba(10,15,22,.88);
  backdrop-filter:blur(18px);
  border-bottom:1px solid #1d2935;
  display:flex;
  justify-content:space-between;
  align-items:center;
}

.logo{
  font-size:19px;
  font-weight:800;
  color:#48ff9b;
}

/* Buttons */
button{
  border:0;
  border-radius:10px;
  padding:8px 12px;
  color:#fff;
  background:#17222d;
  cursor:pointer;
  font-size:13px;
}

/* Hero */
.hero{
  padding:28px 15px 18px;
  text-align:center;
}

.hero h1{
  font-size:28px;
  margin-bottom:7px;
}

.hero p{
  color:#8d9aa6;
  font-size:13px;
}

/* Main */
.container{
  max-width:900px;
  margin:auto;
  padding:12px;
}

/* Search */
.search{
  width:100%;
  height:44px;
  padding:0 14px;
  border-radius:12px;
  border:1px solid #253341;
  background:#101820;
  color:white;
  outline:none;
  margin-bottom:10px;
  font-size:14px;
}

/* Category */
.filters{
  display:flex;
  gap:6px;
  overflow-x:auto;
  padding-bottom:12px;
  scrollbar-width:none;
}

.filters::-webkit-scrollbar{
  display:none;
}

.filters button{
  white-space:nowrap;
  padding:7px 12px;
  font-size:12px;
  border-radius:9px;
}

.filters button.active{
  background:#48ff9b;
  color:#07110c;
}

/* Games */
.games{
  display:grid;
  grid-template-columns:repeat(2,minmax(0,1fr));
  gap:10px;
}

.card{
  background:rgba(18,27,36,.88);
  border:1px solid #243442;
  border-radius:15px;
  overflow:hidden;
}

.card img{
  width:100%;
  height:105px;
  object-fit:cover;
  background:#101820;
}

.card-body{
  padding:10px;
}

.card h3{
  font-size:15px;
  margin-bottom:5px;
  white-space:nowrap;
  overflow:hidden;
  text-overflow:ellipsis;
}

.card p{
  color:#9eabb6;
  font-size:11px;
  margin-bottom:5px;
  line-height:1.35;
}

.meta{
  font-size:9px;
  color:#71808d;
  margin:7px 0;
}

.download{
  width:100%;
  padding:8px;
  background:#48ff9b;
  color:#06110b;
  font-weight:bold;
  font-size:12px;
}

.delete{
  width:100%;
  margin-top:5px;
  padding:7px;
  background:#402027;
  font-size:11px;
}

/* Admin */
.admin-panel{
  display:none;
  margin-bottom:10px;
  gap:6px;
  flex-wrap:wrap;
}

.admin-panel button{
  font-size:11px;
  padding:7px 10px;
}

/* Modal */
.modal{
  display:none;
  position:fixed;
  inset:0;
  z-index:30;
  background:rgba(0,0,0,.72);
  backdrop-filter:blur(8px);
  padding:15px;
  overflow:auto;
}

.modal-box{
  max-width:450px;
  margin:30px auto;
  background:#111a23;
  border:1px solid #293946;
  border-radius:18px;
  padding:17px;
}

.modal-box h2{
  font-size:19px;
  margin-bottom:12px;
}

.close{
  float:right;
  padding:6px 9px;
}

input,
textarea,
select{
  width:100%;
  padding:10px;
  margin:5px 0;
  border-radius:10px;
  border:1px solid #293946;
  background:#0a1118;
  color:#fff;
  outline:none;
  font-size:13px;
}

textarea{
  min-height:75px;
  resize:vertical;
}

.form-btn{
  width:100%;
  margin-top:8px;
  padding:10px;
  background:#48ff9b;
  color:#06110b;
  font-weight:bold;
}

/* Footer */
footer{
  text-align:center;
  padding:25px 10px;
  color:#71808d;
  font-size:11px;
}

/* Small phones */
@media(max-width:380px){

  .games{
    grid-template-columns:repeat(2,minmax(0,1fr));
    gap:8px;
  }

  .card img{
    height:90px;
  }

  .card-body{
    padding:8px;
  }

  .card h3{
    font-size:13px;
  }

  .hero h1{
    font-size:25px;
  }

  .container{
    padding:9px;
  }
}

/* Larger screens */
@media(min-width:700px){

  .games{
    grid-template-columns:repeat(3,minmax(0,1fr));
  }
}
