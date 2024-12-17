import React, { useState, useEffect } from 'react';

function App() {
  const [genderData, setGenderData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [name, setName] = useState('luc'); // Default name 'luc'

  // Fetch gender data for the name
  const fetchGenderData = async () => {
    setLoading(true);
    try {
      const response = await fetch(`https://api.genderize.io?name=${name}`);
      const data = await response.json();
      console.log(data); // Log the response to check the structure
      setGenderData(data); // Set the data to the state
    } catch (error) {
      console.error('Error fetching gender data:', error);
      setGenderData({ error: 'Failed to fetch data' });
    } finally {
      setLoading(false);
    }
  };

  // Fetch data on component mount and when the name changes
  useEffect(() => {
    fetchGenderData();
  }, [name]);

  return (
    <div>
      <h1>Gender Information</h1>
      
      {/* Input for changing name */}
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Enter a name"
      />

      {loading ? (
        <p>Loading...</p>
      ) : genderData ? (
        <div>
          {genderData.error ? (
            <p>{genderData.error}</p>
          ) : (
            <p>
              Name: {genderData.name}<br />
              Gender: {genderData.gender ? genderData.gender : 'Unknown'}<br />
              Probability: {genderData.probability * 100}%<br />
              Count: {genderData.count}
            </p>
          )}
        </div>
      ) : (
        <p>No data found</p>
      )}
      
    </div>
  );
}

export default App;
