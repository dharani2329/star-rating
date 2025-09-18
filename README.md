<!DOCTYPE html>
<html lang="en" ng-app="starApp">
<head>
  <meta charset="UTF-8">
  <title>Star Rating Demo</title>
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.2/angular.min.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin-top: 50px;
    }
    .star-rating {
      font-size: 40px;
      cursor: pointer;
    }
    .star {
      color: lightgray;   /* default */
      transition: color 0.2s;
      margin: 0 5px;
    }
    .star.filled {
      color: gold;        /* when clicked */
    }
  </style>
</head>
<body ng-controller="StarController">
  <h2>⭐ Star Rating Demo</h2>
  <div class="star-rating">
    <span ng-repeat="star in stars track by $index"
          class="star"
          ng-class="{filled: $index < rating}"
          ng-click="setRating($index + 1)">
      ★
    </span>
  </div>
  <p>You rated: {{rating}} / {{stars.length}}</p>

  <script>
    angular.module("starApp", [])
      .controller("StarController", function($scope) {
        $scope.rating = 0;
        $scope.stars = [1, 2, 3, 4, 5];

        $scope.setRating = function(value) {
          $scope.rating = value;
        };
      });
  </script>
</body>
</html>
