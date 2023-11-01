### EXP-11

```
# Sample data
x <- c(1, 2, 3, 4, 5)
y <- c(2, 4, 5, 4, 5)

# Create a linear regression model
model <- lm(y ~ x)

# Plot the data points and regression line
plot(x, y, main="Simple Linear Regression", xlab="X", ylab="Y")
abline(model, col="red")

# Display regression summary
summary(model)

# Predict a value for a new x
new_x <- 6
predicted_y <- predict(model, data.frame(x = new_x))
cat("Predicted Y for X =", new_x, ":", predicted_y, "\n")
```
