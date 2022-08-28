
<html>
    <head>
        <!-- CSS only -->
        <link href="css/bootstrap.min.css" rel="stylesheet" integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx"          crossorigin="anonymous">
        <script
            src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.9.4/Chart.js">
        </script>
    
        <title>Document</title>
    
        <style>
            /* .line {
                border: 3px black ;
            } */
    
        </style>
    
    </head>
    <body style="background-color:rgb(212, 242, 252)">
        <div class="card " style="width: 20rem">
            <div class="card-body">
                <p class="card-text">Some quick example text</p>
            </div>
            <div class="card-img-top" style="width: 100%; ">
                <canvas id="myChart" ></canvas>
                <script >
                    var xValues = [100,200,300,400,500,600,700,800,900,1000];
    
                    new Chart("myChart", {
                    type: "line",
                    data: {
                        labels: xValues,
                        datasets: [{
                        data: [860,1140,1060,1060,1070,1110,1330,2210,7830,2478],
                        borderColor: "red",
                        fill: false
                        },{
                        data: [1600,1700,1700,1900,2000,2700,4000,5000,6000,7000],
                        borderColor: "green",
                        fill: false
                        },{
                        data: [300,700,2000,5000,6000,4000,2000,1000,200,100],
                        borderColor: "blue",
                        fill: false
                        }]
                    },
                    options: {
                        legend: {display: false}
                    }
                    });
                </script>
            </div>
        </div>
    </body>
    
    </html>