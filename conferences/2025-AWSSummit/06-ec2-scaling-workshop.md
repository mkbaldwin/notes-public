# EC2 Scaling Workshop

 * Focus on predictive scaling
 * Tradtional auto scaling
   * Total response time = time to trigger scaling action + time to initialize the instance
   * Pain points
     * Spiky workloads
       * It is inherently reactive so it lags behind the real usage
       * Fine for gradual changes but not for sudden short spikes
     * Long initialization time
       * 
     * Manual scaling
 * Predictive Scaling
   * Launches EC2 in anticipation of demand
   * Uses previous analytic data to determine patterns
   * Proactively manage capacity
   * Helps avoid users having poor response time
   * uses machine learning to predict capacity requirements based on historical data from CloudWatch
   * requires 24 hours of metric history before it can generate forecasts
   * finds patterns in CloudWatch metric data from the previous 14 days to create an hourly forecast for the next 48 hours